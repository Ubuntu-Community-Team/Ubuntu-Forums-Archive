---
title: "change IP inside virtualbox DHCP ?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by mysoogal on 2009-03-15
:(here is my problem, i got Wireless every time a new laptop connects to my wireless it gets IP address of 192.168.2.2 to whatever .2.43 you get the idea.

i believe i have to change the DHCP thing inside xubuntu so it uses from my wireless IP ? 

now the issue i'm having is when i installed xubuntu inside virtualbox, the IP it shows can not be accessed from my wireless connction. i normally want to have access through port 80.

here is the issue. 

[IMG]http://i42.tinypic.com/25podug.jpg[/IMG]

here is my wireless config

[IMG]http://i42.tinypic.com/15ge7es.jpg[/IMG]

i hope someone here can help me out, i just want to have access from outside the virtualbox machine.

---

### Post by theozzlives on 2009-03-15
use your router as a DHCP serrver and assign an IP  to the MAC address and hostname in VirrtualBox

---

### Post by mysoogal on 2009-03-15
> **theozzlives said:**
> use your router as a DHCP serrver and assign an IP  to the MAC address and hostname in VirrtualBox

i believe that's whats already running in my wireless box. 

the issue is, inside xp i have virtualbox with xubuntu, the connection is uses i think its from xp. so xubuntu doesn't talk to my wireless box for DHCP ? something like that

im not sure how to change things like you said in virtualbox there is network settings. no idea how to change it :(


xubuntu is using wired network connection inside virtualbox which is installed on xp, this is really the problem. xubuntu not getting IP from wireless box.

---

### Post by theozzlives on 2009-03-15
> **theozzlives said:**
> use your router as a DHCP serrver and assign an IP  to the MAC address and hostname in VirrtualBox

Nevermind, I just tried it. It don't work like that.

---

### Post by Rocket2DMn on 2009-03-15
In newer versions of vbox, you can go to the Settings on a VM, choose Network, and select Host Interface under "Attached to:"
This will have your local DHCP server (typically, your router) assign a network IP rather than your computer issuing the VM a local IP.  I believe this only works in vbox 2.0 or higher, and no further configuration is needed inside the VM (just get a DHCP IP, as it is by default).  If you don't have an updated version of vbox, or can't get one, then you will have to setup a network bridge.

---

### Post by mysoogal on 2009-03-15
> **Rocket2DMn said:**
> In newer versions of vbox, you can go to the Settings on a VM, choose Network, and select Host Interface under "Attached to:"
This will have your local DHCP server (typically, your router) assign a network IP rather than your computer issuing the VM a local IP.  I believe this only works in vbox 2.0 or higher, and no further configuration is needed inside the VM (just get a DHCP IP, as it is by default).  If you don't have an updated version of vbox, or can't get one, then you will have to setup a network bridge.


thanks dude it works great. i'm able to access it, pretty cool. i can play around now with ubuntu from windows. now i just need to install this putty shell thing so i can send it commands like inside xubuntu :D

yes if your wondering, i upgraded my vbox, it was old version, i thought i had the new version :O

im just wondering, if my wireless IP changes will this auto change inside vbox ?:o

xubuntu is great

---

### Post by carml on 2009-03-15
I think that will change,but I'm not sure.
Everytime I used something under Virtualbox,the machine inside looks attached to a wired connection,independently what the real connection was. :)

---

### Post by mysoogal on 2009-03-15
> **carml said:**
> I think that will change,but I'm not sure.
Everytime I used something under Virtualbox,the machine inside looks attached to a wired connection,independently what the real connection was. :)

yes i just tested it, disconnected my wireless connection and reconnected , vbox got new ip without me doing anything


i think i messed up the ftp server

---

### Post by Rocket2DMn on 2009-03-15
The assignment of your vbox IP is different than your host machine's IP.  They should be able to change independently.  You can configure them completely different (for instance, one can be a static IP, the other can be dynamic).  You just need the correct configuration in the correct place.  The vbox connection won't see a wireless type connection, just its vbox network adapter.

---

### Post by mysoogal on 2009-03-15
> **Rocket2DMn said:**
> The assignment of your vbox IP is different than your host machine's IP.  They should be able to change independently.  You can configure them completely different (for instance, one can be a static IP, the other can be dynamic).  You just need the correct configuration in the correct place.  The vbox connection won't see a wireless type connection, just its vbox network adapter.

here is my config on vbox :D

[IMG]http://i39.tinypic.com/23rwxlk.png[/IMG]

---

