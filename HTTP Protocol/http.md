
Exercice :
| URL                    | Méthode | Code | Content-Type     |
|------------------------|---------|------|------------------|
| httpbin.org/get        | GET     | 200  | `application/json` |
| httpbin.org/post       | POST    | 200  | `application/json` |
| httpbin.org/status/201 | GET     | 201  | `text/html`      |


<img width="551" height="448" alt="image" src="https://github.com/user-attachments/assets/f34f82c6-9b6c-45d3-a6db-81b600e0c787" />
<img width="648" height="218" alt="image" src="https://github.com/user-attachments/assets/878f9854-5e3a-401e-8e1a-d4f8f3dcb335" />

La difference est que -i inclut seulement les headers de reponse + le resultat JSON
Par contre -v montre tous la communication entre le serveur et cURL.

Exercice Avance : 

<img width="914" height="607" alt="image" src="https://github.com/user-attachments/assets/29892721-3779-4a96-b3bd-41dab57d8758" />

Exercice Pratique : 

<img width="1083" height="456" alt="image" src="https://github.com/user-attachments/assets/f9c6e88e-a51a-42c3-9905-3ba1bf94e38d" />

<img width="1089" height="295" alt="image" src="https://github.com/user-attachments/assets/13605a5f-6fe9-49aa-8829-3d82a8c30ff1" />

Exercice : 

| Site | HSTS | X-Frame | CSP | Note |
|------|------|---------|-----|------|
| github.com | Oui | Oui (DENY) | Oui | CSP très stricte, HSTS avec preload, X-Frame DENY |
| google.com | Oui | Oui (SAMEORIGIN) | Non | HSTS actif mais pas de CSP en mode enforce |
| avito.ma | Oui | Non (absent) | Non | HSTS présent (Cloudflare), mais manque X-Frame et CSP |

TP 5 : Cache HTTP
<img width="1077" height="820" alt="image" src="https://github.com/user-attachments/assets/87bbe0f3-5a7b-48b9-b90c-3ebf82688784" />
Network tab après rechargement (F5) – les fichiers sont servis depuis le cache (disk cache) ou avec 304

Les fichiers CSS, JS et PNG sont chargés depuis le cache du navigateur (indiqué par (disk cache)).

La page HTML est revalidée auprès du serveur (statut 304) car elle contient no-cache, must-revalidate.

Exercices Récapitulatifs

1. Différence entre no-cache et no-store
No-cache : le navigateur a le droit de garder la ressource, mais avant de l’utiliser il doit demander au serveur si ça a changé.
No-store : interdit de stocker quoi que ce soit, même pas en cache. C’est plus strict, genre pour des données sensibles.

2. Pourquoi POST n'est pas idempotent ?
Parce que si tu envoies deux fois le même POST, ça peut créer deux ressources différentes (exemple : deux commandes, deux posts sur un forum). Alors que idempotent = le résultat est le même après plusieurs appels. Donc POST c’est pas idempotent.

3. Que se passe-t-il avec un code 301 ?
C’est une redirection permanente. Le navigateur va automatiquement vers la nouvelle URL et ensuite il se souvient que c’est l’adresse définitive. Même les favories sont mis à jour.
4. À quoi sert le header Origin ?
Il donne l’origine de la requête (protocole, domaine, port). C’est utilisé pour la sécurité CORS, pour que le serveur puisse décider si il autorise la requête ou pas. Évite les attaques cross‑site.

5. Pourquoi utiliser HttpOnly sur les cookies de session ?
Pour que le cookie ne soit pas accessible par JavaScript (via document.cookie). Comme ça, même si un attaquant fait du XSS, il peut pas voler le cookie de session. C’est une sécurité importante.
