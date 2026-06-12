---
title: "Connect 2 PC via Ethernet Cable"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by mayagrafix on 2014-09-29
Does I need Standard Ethernet cable or Crossover Ethernet cable to hook up 2 PC running Ubuntu 14.04? 

I just want to transfer some files from one PC to another with minor headaches.}

Thanx!

---

### Post by mayagrafix on 2014-09-29
Already tried Samba. Major disapointment. Says I dont have enough Permissions. Then said it dont support the backend. Then it dont show up at all. :>(

---

### Post by Michael_McKenney on 2014-09-29
You can use a switch and standard CAT 6 cables or a CAT 6 crossover cable.   They need to be in the same workgroup and have the same user and password setup for seamless file transfers.   You need proper permissions on both sides or use super user rights.

---

### Post by MartyBuntu on 2014-09-29
You can use any CAT5/5E/6 cable if either of the machine's NIC's is gigabit capable (crossover switching is done via software built into the NIC's BIOS).
Then, setup ICS (internet connection sharing) on one of the machines. There you have it.

---

