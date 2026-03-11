
# Pour aller plus loin – Projet Docker & Compose

Ces exercices sont **progressifs**.  
Ils permettent d’approfondir le projet sans sortir du cadre Docker / Compose / DevOps.

Ils ne sont pas obligatoires.

## Robustesse (pensée DevOps)

### Objectif
Comprendre que, dans un système distribué, les services **ne démarrent pas toujours dans le bon ordre**.

---

### Gérer le cas où la DB n’est pas prête

#### Constat
- Au démarrage, l’API peut tenter de se connecter à PostgreSQL
- La DB peut ne pas être encore prête

#### À faire
- Mettre en place une logique simple de retry :
  - tenter la connexion
  - attendre quelques secondes
  - réessayer plusieurs fois avant d’échouer

#### Objectif pédagogique
- Découvrir une problématique réelle des systèmes distribués
- Comprendre que `depends_on` ne garantit pas la disponibilité

## Configuration (bonnes pratiques)

### Objectif
Séparer clairement **le code**, **la configuration** et **les secrets**.

---

### Utiliser un fichier `.env`

#### À faire
- Créer un fichier `.env`
- Y placer :
  - `DB_HOST`
  - `DB_USER`
  - `DB_PASSWORD`
  - etc.
- Modifier `docker-compose.yml` pour charger ce fichier

#### Bonnes pratiques
- Ne jamais versionner le fichier `.env`
- Ajouter un fichier `.env.example` documenté

#### Question de réflexion
> Pourquoi les secrets ne doivent-ils pas être dans le code ni dans le dépôt Git ?