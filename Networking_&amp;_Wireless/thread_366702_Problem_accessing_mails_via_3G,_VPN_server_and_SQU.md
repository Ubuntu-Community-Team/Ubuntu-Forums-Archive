---
title: "Problem accessing mails via 3G, VPN server and SQUID"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by Hargael on 2007-02-21
Hello,

First of all excuse me for my english and the mistakes i'll make further. I'm french and i can't find any help on the french ubuntu forums so I try a most visited forum :).

Here's my problem:
I'm deploying a 3G architecture for my company. This means that every computer of my company may be able to access the internet everywhere it can recieve a mobile phone signal.
In order to have access to Internet, i've configured a VPN Server (OpenVPN) on a 6.10 Ubuntu and i've installed SQUID. The computers connect on the 3G network, launch their OpenVPN clients and can browse the web after having the proxy server adress set on Firefox.
And all this is working fine.

The problem is the access for the mails. All computers use Thunderbird client. Thunderbird can't connect to any pop or smtp server (on port 25 or 110). But, i can ping the smtp/pop servers. 
I've read that squid is a web proxy so it won't be useful to forward mail packets. Ok.
At this point, I'm stuck. I can't find any solution for my remote computers to access their mails.

Here's a list of what i've tried and don't work:

		* Changed the proxy settings of Thunderbird to use my proxy server SQUID
		* Activated the ip_forwarding (ipv4)
		* Tried several rules for the linux firewall
		* Deleted all the firewall rules and set the default policy to "ACCEPT"
		* Even added the 25 and 110 ports to squid.
		
I would really appreciate some help for this problem. Any clue will be welcomed.

Following, my original message on the French Ubuntu Forum.

Thanks.

Hargael.
------------------------------------------------------------------
***************************************************
------------------------------------------------------------------


Bonjour,

Je vous présente mon problème qui est sommes toutes assez simple. Je suis en train de deployer une architecture 3G pour mon entreprise afin de lui offrir plus de mobilité.
Avec un abonnement 3G/3G+, il n'est pas possible (à moins de payer évidemment) d'avoir accès directement au WEB. Aussi la ruse consiste à utiliser une tunnel VPN qui arrive sur un serveur sur lequel un proxy redirige vos demandes sur le WEB.

Tout ceci fonctionne très bien. J'ai des portables en 3G qui se connectent à mon serveur UBUNTU sur lequel tournent OpenVPN pour les tunnels VPN et SQUID pour les redirections de pages WEB.
Une modification dans les paramètres des navigateurs WEB afin de leur dire d'utiliser le proxy et on peut naviguer sur le web partout ou on capte.

Tout ne pouvant être aussi facile, j'ai fini par tomber sur un problème auquel je ne trouve pas de solution...
En effet, la récupération des mails est impossible (pour le moment). En fait, je ping bien les serveurs pop et smtp que je veux contacter, mais quand il s'agit de s'adresser à eux sur les ports 110 et 25, plus rien ne fonctionne.

Après avoir cherché pas mal de temps voici en résumé les choses que j'aie déjà faites pour essayer d'accéder à mes mails sur mon Thunderbird en 3G.

  * J'ai évidemment changé les paramètres réseau du Thunderbird pour qu'il passe par le proxy.
  * J'ai activé l'ip_forwarding sur mon serveur Ubuntu (ipv4)
  * J'ai fait un mix des règles iptables que j'ai trouvées sur le net pour l'adapter à ma configuration, sans succès.
  * J'ai supprimé toutes les regles de firewall en mettant une politique par défaut en "ACCEPT" sur mon serveur.
  * J'ai même essayer de faire prendre en compte les ports 25 et 110 à SQUID mais ça ne semble rien changer...

Donc je dois bien avouer que je seche là. Non seulement ça ne marche pas, mais le pire du pire, c'est que je ne comprends pas pourquoi.

Si une âme charitable pouvait prendre le temps d'illuminer ma lanterne, ça me renderait bien service.

En vous remerciant d'avance.

Hargael.

---

### Post by Hargael on 2007-02-22
Any idea about my mail access via VPN problem ?

---

### Post by Hargael on 2007-02-23
As SMTP and POP seems no to be proxyable, I dropped the idea to set a proxy server in the Thunderbird configuration.

I tried to add a route on my remote machines to the SMTP and POP servers but it still doesn't work.

Any idea on this subject may help me :)

---

### Post by Hargael on 2007-02-28
Nobody ?

---

