---
title: "can anyone help i think i close to gettin my network card to work"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by notsteve on 2007-04-03
now i have a broadcom network card, i`v gone through all the steps and the driver bcml5 is installed and present but the light to show the network card is not working.

all the steps go fine until i write:
steve@steve-laptop:~$ sudo ndiswrapper -m
then this pops up:
modprobe config already contains alias directive
is this normal, if so why does my network card not work.
Edit/Delete Message

---

### Post by kerry_s on 2007-04-03
Try installing ndisgtk, then look under administration>install windows drivers. It's a gui for ndiswrapper it will do all the work with simple point and click.

---

### Post by notsteve on 2007-04-03
i did, but i can't install it cause i already installed it manually

---

