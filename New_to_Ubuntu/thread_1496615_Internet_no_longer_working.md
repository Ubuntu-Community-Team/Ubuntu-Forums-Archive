---
title: "Internet no longer working"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Julia A on 2010-05-29
Hi
I installed Ubuntu 9.1 on my eee 900 a few weeks ago, but found I couldn't access the internet. I left it alone, but yesterday decided to have another go, and to my surprise I was able to connect (initially using ethernet, but then able to switch to wireless). 
I downloaded various updates last night, and all was fine today. However, I was fiddling around, trying to access my network from the eee, when I realised that it could no longer connect (the wireless icon on Ubuntu had disappeared, although the wireless light on the eee was still alight). I therefore reconnected the ethernet cable, but still cannot connect.

I did a bit of searching, and found the instruction to put sudo pppoeconf into the terminal. I entered my password, and the system was searching, but eventually came up with the following:
"Sorry I scanned 2 interfaces but the Access Concentrator of your provider did not respond. Please check network and modem cables. Another reason for scan failure may also be another running pppoe process with controls the modem". 

I've checked cables etc; my network generally is running fine (with Windows). I've removed Firestarter and Etherape that I installed yesterday). One problem is that I don't seem to have "Network" under System, so I can't do any configuring of the network. And as I don't have an internet connection I can't install it!

Grateful for any advice, please, in a way that a complete newbie can understand!

Many thanks

---

### Post by candtalan on 2010-05-29
I have an asus eee900 and although I am not sure now what internet connectivity I found with ubuntu 9.10, the 10.04 works ok including with wireless. I use both 10.04 from a live usb stick, and an installed Ubuntu netbook remix. both pick up the eee900 wireless immediately.

Incidentally, easypeasy, which is based on ubuntu, also works well on the machine, including networking.

---

### Post by Julia A on 2010-06-01
Thanks for your help, Candtalon. While I'd hoped to be able to find some setting that would enable me to connect, eventually I decided to go the upgrade route. I downloaded 10.04, installed it, and I can now access the internet either through wireless or ethernet cable.

---

