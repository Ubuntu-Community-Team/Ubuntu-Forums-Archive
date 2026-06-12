---
title: "Single Network Adapter Appears as 'eth1'"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by Avian00 on 2006-08-24
I'm running Ubuntu Server (no GUI).  I have only one network adapter on my computer, but it shows up as eth1.  How is this possible?  Shouldn't it be eth0?  Can somebody please explain how adapters get assigned their 'eth' # and how I can fix this so this adapter becomes 'eth0'?  For now, I've had to modify my /etc/network/interfaces file to use 'eth1' instead of 'eth0'.

---

### Post by Original Brownster on 2006-08-24
Hi,
Very strange, AFAIK linux numbers them as found sequentially therefore it would suggest there is another one! Dont suppose it's an 'on board' controller youve overlooked?

Whats the output of :

$ dmesg | grep 'eth'

and

$ ifconfig -a

cheers,

---

