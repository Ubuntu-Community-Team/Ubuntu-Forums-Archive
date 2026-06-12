---
title: "I am pulling my hair out"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by lonce on 2006-10-26
Anyone know how to get a linkskey pci 802.11 G wireless card working.

Used ndiswrapper and it recognizes it and i can set it up.  But it will not connect.  It wont connect to my router.  Everything says its working ok, yet it will not connect what so ever.  I dont get it.

---

### Post by towsonu2003 on 2006-10-26
if you have one, take down your wired device and see if it works: 
sudo ifconfig eth0 down 

eth0 -> your wired interface / device

---

### Post by dmizer on 2006-10-27
which wireless g card is it (version number)?

if you don't know, post the output of 'lspci' and 'cardctl ident'.

---

