---
title: "Nabaztag: unbelivible, impossible to connects"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by dentaku65 on 2007-11-16
I'm trying to connect to the rabbit [Nabaztag]("http://www.nabaztag.com") to configure it to my wi-fi connection (and let him go on internet), but... I'm not able to do it!
I've tried everything:
knetworkmanager
wifi-radar
wlassistant
scripting with iwconfig

Nothing to do!
This rabbit have a silly wi-fi connection with no encription to reach him and configure to your wi-fi connection through web interface, I supposed should be a really no-thinking operation, but no way from kubuntu... the worst thing is that under xp home was configured in 30 seconds... no good...

:(

---

### Post by arnaudv6 on 2008-01-16
I got the same problem :
knetworkmanager stops while waiting for an IP....
Searching :(
(got a centrino wifi, with ipw2100 mod loaded)
can't stand what's not going on :(

---

### Post by arnaudv6 on 2008-01-25
Je crois avoir trouvé une solution existante :

[http://nabaztag.forumactif.fr/mise-en-route-du-lapin-f1/pour-les-linuxiens-t7251.htm]("http://nabaztag.forumactif.fr/mise-en-route-du-lapin-f1/pour-les-linuxiens-t7251.htm")

La vie de SixV mon Nabaztag/tag va pouvoir suivre son cours
:)

Edit : sorry :$,
then in english, as far as I can do this :
The aim is just to overpass the dhcp option by a hand-made one :
192.168.0.2 for the ip
255.255.255.0 for the masq
Linux was waiting for a dynamic adress, it won't wait anymore,
don't try to ping the rabbit : it won't answer,
but just restart the network services,
and connect to the rabbit : It should work
Hope it will help

---

