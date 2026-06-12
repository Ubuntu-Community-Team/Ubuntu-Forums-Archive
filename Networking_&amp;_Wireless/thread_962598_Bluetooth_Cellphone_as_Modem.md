---
title: "Bluetooth Cellphone as Modem"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by CyberCowboy on 2008-10-29
What is the easiest way to use my cellphone as a modem via bluetooth?

Specifics:

Phone is a Alltel Hue (Samsung R500)
using Ibex RC
Laptop has usb bluetooth fobb
Laptop is a Dell Latitude D530

I was under the impression that Network Manager in Intrepid would allow this natively but either it's not there or I'm dense.

---

### Post by Ghilteras on 2008-11-01
anybody managed to setup a bluetooth cellphone as 3g/gprs modem in intrepid?

---

### Post by shinoj on 2008-11-11
everything works in intrepid. initially i too faced problems in connecting gprs through bluetooth. it failed the first time. then i learnt that one has to execute the connection command with root priviledges. just add sudo before giving the command.
sudo pon XXXXX

this will do the work. 

i hope you know how to set up a rfcomm modem. just google up find how to set it up.

---

