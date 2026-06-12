---
title: "Connecting to wireless network causes laptop to lock-up"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by canada4ever on 2007-12-17
Hey Everyone!

It's been a few months since I've used Linux extensively... But my new Vista laptop has finally driven me back to Linux.  I wanted to start using Ubuntu as my main OS but there are a few things that are holding me back... the biggest thing is that whenever I try to connect to a wireless network with my laptop it lets me see the network enter my key and everything is fine... but as soon as I try and connect my laptop freezes up and the Lock Indicator light on my keyboard starts flashing... I can't do anything and have to reboot.  I'm running Ubuntu 7.10 on a Gateway MT3705 laptop.  I have the same problem both with the Live CD and when it is installed to my hard drive.   This is my first time using Ubuntu and I really appreciate the help.  The sooner I can get rid of my windows install the happier I will be! 
Thanks in advance!
Matthew!

---

### Post by canada4ever on 2007-12-18
Any ideas folks?  I really want to get this working :(

---

### Post by petteriIII on 2007-12-19
I had same problem when trying to use Wireless in 7.10; 7.06 was OK. It turned out that before trying to go to Wireless you must first go to terminal and give the command: sudo /etc/init.d/networking restart  . Hope it works for you too.

---

### Post by canada4ever on 2007-12-20
Hmmmm.... thanks for the tip but it's still not working...... :(
Thanks!

---

