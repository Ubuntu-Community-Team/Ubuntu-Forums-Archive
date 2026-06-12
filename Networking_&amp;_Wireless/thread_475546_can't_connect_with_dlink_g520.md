---
title: "can't connect with dlink g520"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by davidbair on 2007-06-16
Hi, i just installed the most recent version of Ubuntu for the first time and most of the stuff i needed to go with it. The only problem left (to my knowledge) is the internet. I use a D-Link Wirelss G520 network card and i'm having some trouble connecting to my network. The wireless connection icon is in the top right hand corner, but whenever i select my network it tries to connect for a while but then just gives up and stops. And i'm not sure if this is relevant, but my internet connection is Telstra Bigpond Broadband.

Thanks.

P.S. I am currently on a laptop with windows xp installed. It is, at this point, the only way for me to connect to the internet.

---

### Post by bigken on 2007-06-16
try this in a terminal 

sudo iwconfig ra0 essid (name of network)

sudo dhcliednt ra0

---

### Post by davidbair on 2007-06-16
sorry for the stupid question but what would i type in for "name of network"

---

### Post by bigken on 2007-06-16
the name your router uses

---

### Post by davidbair on 2007-06-16
how can i find that name?

---

### Post by bigken on 2007-06-16
type 192.168.0.1 or 192.168.1.1 in your browser this will bring up your router interface 

the user name is normally admin and password is either admin or password

---

### Post by davidbair on 2007-06-16
two problems

1. whenever i type either of those addresses into firefox, it gives an error about the server being busy.

2. when i type it into my laptop i can't get the admin and password right (i don't think the defaults are working)

is there anything relating to the wireless card that i have to manually install? i assumed that it was all installed when the icon for wireless internet came up

---

### Post by bigken on 2007-06-16
you must know the names and password for your router who set it up in 1st place what make is it ?

---

### Post by davidbair on 2007-06-16
D-Link DI-624+

That's the model of the wireless router

---

### Post by bigken on 2007-06-16
dont you have the manual if not download it from web this will tell you everything you need to know

---

