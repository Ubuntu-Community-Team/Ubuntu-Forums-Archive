---
title: "Problem with ppp an proxy connections"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by goo25 on 2008-09-03
nm-applet works fine with any wireless connection, including vpn's. Also with wired connections I have no trouble, but I'm unable to get firefox working when connecting with ppp (I'm using kppp with huawei 226) and skype or other applets like weather on AWN connects without trouble. I suppose it's something with DNS not properly configured. Is it automatically configured?  

When connected with ppp this is route -n output

goo@goo-laptop:~$ route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

---

