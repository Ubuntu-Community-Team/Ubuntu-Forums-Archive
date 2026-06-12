---
title: "how to change eth1 back to eth0"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by pagingmrherman on 2006-10-25
Hi, I took a hard drive w/ ubuntu installed on it out of one PC and stuck it in a totally different other PC.  Everything is working ok but the new NIC is a different type than the old one and it is now eth1 instead of eth0.  

Where does 'eth0' come from?  I'm guessing that there's an alias somehow connected to the old ethernet card's kernel module but I can't for the life of me find it.  I just want to delete the old eth0 and set eth1 back to eth0.

Any help would be appreciated.

Shawn

---

### Post by MyAnda on 2006-10-25
try looking at /etc/iftab

---

### Post by MJN on 2006-10-28
Indeed - I tripped over this one only a couple of days ago too.

As MyAnda says, /etc/iftab holds the key - put your 'new' MAC address in for eth0.

My follow-on question - what/who is responsible for populating /etc/iftab in the first place? Is it done during general installation? A particular (network related) package?

Mathew

---

### Post by MyAnda on 2006-10-30
"man iftab" reports:

The  file /etc/iftab contains descriptive information about the various network interfaces and is used by udev(8) and  its  iftab_helper(8)  to assign consistent names to network interfaces......

looks like udev is your man (...or woman (life of brian reference))...

---

