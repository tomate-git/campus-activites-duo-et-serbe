# Campus activités

Maquette de départ du projet BTS SIO SLAM. Ouvrez le cahier des charges Word situé à côté de ce dossier dans le ZIP.

## Lancer la maquette

1. Extrayez le ZIP. Ouvrez un terminal dans `campus-activites`, le dossier qui contient ce README.
2. Vérifiez PHP avec `php -v`. Sous Wamp, si la commande est introuvable, utilisez le chemin de `php.exe` indiqué par le professeur.
3. Lancez `php -S 127.0.0.1:8000 -t public` et laissez le terminal ouvert.
4. Ouvrez <http://127.0.0.1:8000/> et cliquez sur **Consulter le catalogue**. La maquette affiche trois activités fictives sans base de données. Arrêtez le serveur avec `Ctrl+C`.

Si le professeur fournit une adresse via Wamp/Apache, utilisez celle-ci avec `public/` comme racine web. Le serveur PHP intégré est réservé aux essais locaux. La feuille Bootstrap 5.3.8 est chargée depuis [jsDelivr](https://getbootstrap.com/docs/5.3/) et nécessite un accès réseau. Le contenu reste consultable sans cette feuille.

## Passer au catalogue SQL

1. Démarrez MySQL ou MariaDB. Vérifiez que le PHP utilisé pour lancer le site charge `pdo_mysql` (`php -m`).
2. Importez `sql/01_activite.sql` avec phpMyAdmin. Si vous avez une base imposée et des droits limités, sélectionnez cette base et importez une copie du script dont les deux instructions `CREATE DATABASE` et `USE` ont été retirées. Ajustez le nom dans la configuration locale.
3. Copiez `config/connexion.exemple.php` en `config/connexion.local.php`, puis adaptez le nom de la base, le port et vos identifiants. Le fichier local est ignoré par Git. Vérifiez-le avec `git status --ignored` une fois le dépôt créé.
4. Dans `public/activites.php`, chargez `src/bdd/connexion.php` avec un chemin basé sur `__DIR__`, appelez `connecterBase()` et remplacez les données de démonstration par le résultat de votre requête. La connexion est fournie. Les requêtes et la fiche de détail font partie du travail demandé.
5. Vérifiez la provenance des données en modifiant provisoirement un titre dans votre base de test, puis rechargez la page. Rétablissez le titre après le test.

## Se repérer

| Dossier | Rôle |
|---|---|
| `public/` | Pages et ressources accessibles au navigateur |
| `src/` | Inclusions PHP, données de démonstration et connexion PDO |
| `config/` | Exemple versionné et configuration locale à créer |
| `sql/` | Script initial, puis scripts d’évolution du binôme |
| `docs/` | Notes de conception, scénarios de test et suivi des rendus |

Git se lance à la racine de `campus-activites`. Si vous poursuivez dans le dépôt de la première séquence, intégrez cette base dans ce dépôt et vérifiez les différences avant de committer. Si vous partez du ZIP, un membre initialise le dépôt, puis le publie et invite son partenaire. Le partenaire clone le dépôt commun. Consultez la séance Git pour la procédure sur `main`.
