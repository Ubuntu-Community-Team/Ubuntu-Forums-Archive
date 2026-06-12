---
title: "Setting Up Network"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by spazgda on 2005-05-30
I am trying to get Ubuntu to connect to the internet through a switch.  I currently have a windows box which is connected through the switch fine, and I can directly connect to my cable modem and the Ubuntu Box will connect to the internet.  But how can I make Ubuntu connect to the internet through the switch, the Networking Configurator is not really helping.

---

### Post by elatomo on 2005-05-31
[QUOTE=spazgda]I am trying to get Ubuntu to connect to the internet through a switch.  I currently have a windows box which is connected through the switch fine, and I can directly connect to my cable modem and the Ubuntu Box will connect to the internet.  But how can I make Ubuntu connect to the internet through the switch, the Networking Configurator is not really helping.[/QUOTE]
 
First of all excuse me for my english...

As far as i know, you should set your linux box to act like a "router", you would need two ethernet cards installed in your linux machine, one card (for example eth0) connected to the cable modem and the other connected to the hub/switch, and then set iptables/netfilter in the linux box with the apropiate set of rules to share the internet connection with the other computers (i'm sorry i couldn't help you with more details about this process)

Give a look to this page if you understand spanish: [http://www.zonasiete.org/docs/comp_conc_cable/](http://www.zonasiete.org/docs/comp_conc_cable/)

---

