---
title: webhook teams
description: comment creer un webhook
published: true
date: 2020-05-29T21:25:01.951Z
tags: webhook,ingoing
---
# Création d'un webhook entrant dans ms teams

La documentation permet de créer un webhook entrant dans ms teams, ainsi une application pourra envoyer des messages dans un channel teams

Lancer le client msteams   
Ensuite aller dans le channel où il faut créer le webhook   
Appuyer sur le bouton "+" pour lancer le menu suivant   

![Conversion](1.png "conversion")  

Cliquer sur "Gérer les applications"

![Conversion](2.png "conversion")   

Choisir "Incoming webhook"  

![Conversion](3.png "conversion")  

Cliquer sur "Ajouter à une equipe"   

![Conversion](4.png "conversion")  

Choisir le nom de l'equipe dans le champ prévu puis cliquer sur "Configurer un connecteur"   

![Conversion](5.png "conversion")   

Le champ indiqué "un nom" sera le nom de l'emetteur des messages quand on executera l'application   

![Conversion](6.png "conversion")   

Choisir une image, puis cliquer sur "Créer" 

![Conversion](7.png "conversion")  

Sauvegarder le lien fournit car il sera utilisé pour faire des tests du webhook   

![Conversion](8.png "conversion")   

 ## Test simple 
 
 on peut realiser un test avec une commande curl
 
 
fichier message.json
```
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Alertmanager closed a task",
    "sections": [{
        "activityTitle": "![TestImage](https://47a92947.ngrok.io/Content/Images/default.png)Alertmanager closed a task",
        "activitySubtitle": "System Up",
        "activityImage": "",
        "facts": [{
            "name": "Nom serveur",
            "value": "ctsr1347"
        }, {
            "name": "Alerte",
            "value": "ping OK"
        }],
        "markdown": true
    }]
}
```

On realise un test en remplacant les XXX par le lien obtenu dans l'etape précedente   

```
curl -X POST -d @message.json "https://outlook.office.com/webhook/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```



