---
title: "Feisty to XP ICS"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by ghstzr0 on 2007-07-24
I have a very irritating problem.  I want to set up ICS between my desktop and laptop.  Here's out they're configured...

ROUTER(INTERNET) ----->  DESKTOP (UBUNTU 7.04 x86_64)  ------> LAPTOP (XP PRO)

I HAVE TWO NIC'S ON THE DESKTOP AND A CROSSOVER CABLE!!

I can access the internet on my desktop (I am now...), but I can't seem to get ICS working! :confused::confused:

I removed network-manager because it was wanting to only let one interface be up at a time, and plus I don't need it...

Here's what I've done...
1) I've enabled eth1 (the card connected to the internet) with DHCP. (this works...)
2) I've set eth0 (the other NIC) to static mode with IP address 192.168.1.1
3) I've set my ethernet adapter on my XP laptop to have a static IP of 192.168.1.2
4) Both eth0 and XP adapter have subnet of 225.225.225.0!

I can ping 192.168.1.1 from my xp laptop and get a reply (but NO INTERNET!!!)
I CANNOT ping 192.168.1.2 from Ubuntu and get a reply!!!

What do I need to DO???  I've tried installing firestarter and enabling ICS - but that did nothing!!!

---

### Post by ghstzr0 on 2007-07-24
getting buried already! --> bump

---

