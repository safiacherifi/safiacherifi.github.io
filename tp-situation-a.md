# Remplacement d'un switch d'étage saturé

[← Retour au portfolio](tp-camille.html)

*PME de métallurgie, 45 postes, site principal — mars 2026 — option SISR*

## Contexte

Le site principal compte 45 postes, dont 12 dans l'atelier, reliés à un switch d'étage installé en 2016. Les postes de l'atelier servent aux plans de fabrication et à la saisie des temps.

## Problématique

Depuis trois semaines, les 12 postes de l'atelier subissaient des coupures réseau de quelques secondes, plusieurs fois par jour. La sauvegarde du serveur de fichiers, lancée à 12 h, durait 42 minutes au lieu des 6 minutes habituelles et terminait parfois en erreur.

## Démarche

J'ai d'abord relevé les débits depuis un poste de l'atelier : 8 Mo/s en copie vers le serveur, contre 74 Mo/s depuis un poste du bureau. Trois hypothèses : le câblage, la carte réseau des postes, le switch.

J'ai écarté le câblage : les liens ont été certifiés en 2023 et un test au testeur de câble sur trois prises n'a rien montré. J'ai écarté la carte réseau : le problème touchait les 12 postes, pas un seul.

Restait le switch, un modèle 16 ports à 100 Mb/s dont les compteurs affichaient des erreurs de collision. Je l'ai remplacé par un switch administrable gigabit prêté par le fournisseur, pour valider l'hypothèse avant tout achat.

## Outils mobilisés

- Switch administrable 16 ports gigabit (modèle de prêt, puis modèle acheté)
- Testeur de câble RJ45
- Wireshark 4.2 pour observer les retransmissions
- GLPI 10.0 pour le suivi du ticket et la mise à jour de l'inventaire

## Précautions prises

J'ai sauvegardé la configuration de l'ancien switch, étiqueté les 16 câbles avant de les débrancher, et programmé l'intervention entre 12 h 30 et 13 h 15, hors production. J'ai prévenu le chef d'atelier la veille.

## Résultats

Le débit de copie est passé de 8 Mo/s à 74 Mo/s. La sauvegarde est redescendue à 6 minutes. Aucune coupure signalée dans les trois semaines qui ont suivi. L'inventaire GLPI a été mis à jour le jour même.

## Bilan personnel

J'ai perdu deux jours à suspecter le câblage alors que les compteurs d'erreurs du switch donnaient la réponse dès le premier relevé. La prochaine fois, je commencerai par interroger les équipements réseau en SNMP avant de tester les liens un par un.

---

## Situation B

## Contexte

Le bureau d'étude dispose de 20 postes accessibles par tout le monde. 

## Problématique

Depuis environ deux semaines, un ordinateur du bureau d'étude était défectueux. Il redémarrait plusieurs fois dans la journée, ce qui entraînait une perte du travail de l'utilisateur.

## Démarche

J'ai commencé par regarder l'Observateur d'événements pour chercher l'origine des redémarrages. J'ai remarqué la présence de Kernel-Power 41. J'ai d'abord vérifié si le problème pouvait venir de Windows et effectué les mises à jour disponibles, mais ça n'a pas résolu le problème. J'ai alors pensé a la RAM et lancé un memtest une nuit, mais il n'y avait rien. J'ai donc ouvert le boitier du PC et constaté qu'il y avait énormément de poussière et un bruit bizarre venant du ventilateur. J'ai alors mesuré la consommation éléctrique avec une prise wattmétrique, le poste tirait 310 W en pointe avec une alimentation de 350 W. J'ai donc finis par changer l'alimentation pour une de 550 W, et ensuite fait un nettoyage complet du poste. 

## Outils mobilisés

- memtest
- prise wattmétrique
- alimentation 550 W

## Précaution prises

J'ai débranché le poste avant l'intervention pour travailler en sécurité, et j'ai également vérifié les mises àjour Windows. 

## Résultat

Arrêt des redémarrages pendant le mois suivant. 

## Bilan personnel

C'était ma première panne matérielle trouvée tout seul, et j'en était particulièrement fière. Je penserais donc a vérifier l'alimentation plus tôt la prochaine fois. 

**Compétences mobilisées** : gérer une panne matérielle ; changement d'alimentation.






















