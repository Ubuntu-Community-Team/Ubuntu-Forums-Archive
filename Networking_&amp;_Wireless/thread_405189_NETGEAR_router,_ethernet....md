---
title: "NETGEAR router, ethernet..."
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by FuturisticKid on 2007-04-09
I'm a beginner and at the moment I'm struggling connecting to the internet via ethernet on a pc I have Ubuntu on... At the moment I am on a wireless belkin connection upstairs (windows), works perfect!

My router is: NETGEAR DG

My ethernet card is: SiS900 PCI Ethernet

I tried "$ sudo ifconfig" in terminal and it asked me for a password but it wouldn't let me type anything in. :confused: 

I would be very grateful if you could help, thank you... :)

---

### Post by FuturisticKid on 2007-04-09
Oops ok the terminal worked after and it dectected more results for something called loopback, the only thing there mainly of any sign for ethernet was this...

HWaddr: 00: 10: DC: 8C: D1: CA
MTU: 1500

---

### Post by rolando on 2007-04-09
1. 
You can enter a password, its just blank and you cant see what your typing, but try the password you login with. It will work.
2.
If you are using Gnome, go to system > Administration > Networking

You should be able to sort yourself out from here.

Failing that type in a terminal

sudo network-admin

Which will launch the same application.

:)

---

### Post by FuturisticKid on 2007-04-09
Thanks, will have a go a bit later since small things can stress me out, lol. I didn't think but I know my wireless device can be plugged from one place to another and that is on now so I'm kind of satesfied now that I have the internet wokring down here. Sorry if it was a waste of thread.

---

### Post by rolando on 2007-04-09
No worries.

---

