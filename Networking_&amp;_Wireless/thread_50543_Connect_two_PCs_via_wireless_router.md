---
title: "Connect two PCs via wireless router"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-07-20
Hi guys. Sorry for a stupit question, but I am a complete newb in networking. I bought myself a laptop and installed Ubuntu. Now I want to connect to my desktop PC and have no idea what to do. Basically I've got a wireless router. My desktop PC is connected to it via Ethernet. My laptop is connected via a wireless bridge (I should get a PCMCI card later this week) to the router as well. It works fine, I've got Internet. 

I guess that both my computers are in the network now. But how can I share files on my desktop with laptop?

---

### Post by az on 2005-07-20
By default, Ubuntu can see other networks, but does not talk to them.  To make Ubuntu available to others (talk to the network) install samba.

Then go into System - Administrations - Shared Folders.

---

### Post by foxy123 on 2005-07-21
wow! it is so simple... now I am waiting for my wireless pcmci to make sure it will work  :)

---

### Post by foxy123 on 2005-07-21
What about Windows PC. My desktop is dual-boot and I need an access to it whether it's booted in Windows or Ubuntu. I tried to run WinXP Network Setup Wizard and shared a folder. I see the computer in the Places/Network Servers, but when I click on it I've got```
The folder contents could not be displayed
```. 

Another question is how I can access Ubuntu partition if the PC is booted in Windows?

---

### Post by foxy123 on 2005-07-21
[QUOTE=foxy123]What about Windows PC. My desktop is dual-boot and I need an access to it whether it's booted in Windows or Ubuntu. I tried to run WinXP Network Setup Wizard and shared a folder. I see the computer in the Places/Network Servers, but when I click on it I've got```
The folder contents could not be displayed
```. [/QUOTE]

well, it's solved: I completely forgot about Sygate firewall on my WinXP, have not logged in to it for ages :)

> Another question is how I can access Ubuntu partition if the PC is booted in Windows?
this question still stands however...

---

### Post by Tremblay on 2005-07-27
[QUOTE=foxy123]Another question is how I can access Ubuntu partition if the PC is booted in Windows?[/QUOTE]
Explore2FS allows you to access your Ubuntu/Linux partition from a Windows boot. More information here:  [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by foxy123 on 2005-07-27
[QUOTE=Tremblay]Explore2FS allows you to access your Ubuntu/Linux partition from a Windows boot. More information here:  [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)[/QUOTE]
Thanks for the tip, butbi am not sure if it is what I need. I actually need to access Linux partitions, which are on the Windows booted PC, from a Linux machine.

---

