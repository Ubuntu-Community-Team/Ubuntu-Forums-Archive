---
title: "Can't Read /etc/network/interfaces"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by itzpapalotl on 2007-06-29
!
Well, having solved my last set of issues with the RAID, I am now running in to a weird one.

I set up a server. 6.06 dapper. It's all fine. Runs great EXCEPT
it won't connect to the internet. 
or the local.
I need it on a static. I know I have /etc/network/interfaces configured correctly, but for the record:, the stuff that is NOT commented out  is

#  loopback
auto lo
iface lo inet loopback

#  Natalie Alpha
auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.254

#  Natalie Beta
auto eth1
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.254


------ Petty much your standard interfaces file
so when I give it a kick (sudo ifdown eth0)
/etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

But... I can nano it just fine.
and.. Uh.... it sure is there all right..

This is weird.. anybody else come against this?

---

### Post by moron on 2007-06-29
Sounds like a typo in the interfaces file. The complaint is not about file permissions, it is  about syntax.

Cheers

---

### Post by itzpapalotl on 2007-06-29
In the configuration script itself? 
Well, No. I re-keyed it making ure about things like control keys and caps.
Same problem. 
Is this maybe related to the RAID device. I have my whole / system on a big RAID 5, but /boot and SWAP are not in there. SWAP is in it's own little 100 gig RAID 0 Array for speed, and /boot lives alone a the beginning of the first drive. could this be a RAID issue. It seems unlikely as all the other things from / work. like, you know... The Operating System.

---

### Post by itzpapalotl on 2007-06-29
No, No.. sorry. You were right. Had a missing # way way way deep in the last guy's notes on interfaces.
Thanks.
Resolved.

---

