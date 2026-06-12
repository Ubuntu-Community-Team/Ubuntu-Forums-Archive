---
title: "[SOLVED] Atheros does not reconnect..."
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by CasPol on 2008-06-09
Hi there;

I have managed to get my Atheros 5212 wireless card working in Hardy Heron. However one problem remains, the card does not pick up my home metwork after I restart my computer... I have to add all the details all over again, each time I restart...

Any advise anyone ?

Many thanks ..

---

### Post by attari on 2008-06-09
> **CasPol said:**
> Hi there;

I have managed to get my Atheros 5212 wireless card working in Hardy Heron. However one problem remains, the card does not pick up my home metwork after I restart my computer... I have to add all the details all over again, each time I restart...

Any advise anyone ?

Many thanks ..


I had similar problem in 7.04 I recall... just forgot the exact workaround... :(

As far as I can remember it had to do with keeping wired connecion on static IP... or was it keeping it on dhcp?....hmmm.. try both! :lolflag:

In the network configuration manager window press save button to save the setting for your wifi, so you can select it from drop down menu in future.

---

### Post by bmwman on 2008-06-09
sudo gedit /etc/rc.local and add a new line above 'exit 0':

Code:/etc/init.d/networking restart

i had the same problem but it works fine now.

---

### Post by bmwman on 2008-06-09
> **bmwman said:**
> sudo gedit /etc/rc.local and add a new line above 'exit 0':

Code:c
i had the same problem but it works fine now.

sorry, just add /etc/init.d/networking restart, without 'code;'

---

