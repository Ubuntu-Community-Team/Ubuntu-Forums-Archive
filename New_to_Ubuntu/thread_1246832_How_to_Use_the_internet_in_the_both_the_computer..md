---
title: "How to Use the internet in the both the computer."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by imran_khan on 2009-08-22
**[SIZE=5]i have one laptop and  one desktop i want to use the internet in both the system[/SIZE]****[SIZE=5] .we have atteched both the system with the LAN CARD but not yet we use internet in the both the computer simantanously[/SIZE]** [B][COLOR=Black][SIZE=5]
[/SIZE][/COLOR][SIZE=5]plz give step  to use the internet in both the computer .we are both using ubuntu in both the system, and the desktop computer we want to make host ..... how[/SIZE] [/B][INDENT][SIZE=5][COLOR=Black][B]plz reply as soon as  i am the biggner in the linux .
plz give the detail in breif.
possible.....thanx to all[/B] the linux community to make that platporm to give the approunity to all the user ..
[/COLOR][/SIZE][/INDENT]

---

### Post by jbeukema on 2009-08-22
Could you repeat that in English, please?

You tried to plus two computers into one card? :confused:

---

### Post by fraser_m on 2009-08-22
You have the desktop connected to the internet, and want to connect the laptop over LAN, right? Install Firestarter on the desktop:
```
sudo apt-get install firestarter
```

Then follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)

---

### Post by 3rdalbum on 2009-08-22
How are you connected to the Internet?

If you have a broadband router, then you need to plug both computers directly into the router. If the broadband modem only has one Ethernet (LAN) port, then you need an Ethernet hub, switch or router with at least 2 Ethernet ports. Plug the hub/switch/router into the modem, and then the computers into the router.

---

