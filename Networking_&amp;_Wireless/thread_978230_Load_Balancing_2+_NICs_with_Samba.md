---
title: "Load Balancing 2+ NICs with Samba"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Bleek_II on 2008-11-10
Hi,
I'm trying to setup a file server in a computer lab at my university. The computers in the lab are running Windows XP and once a week I need to distribute large files (10GB+) to all of them. The file server is running 8.04 with two NICs, though it will soon have three.
My hope is to have it setup so that...
A. The two NICs showup on the windows network as two computers that let me access the same files
or
B. The two NICs load balance the bandwidth.

Notes: 
1. I'm not a highly skilled linux user, I'm just a user. 
2. I don't have access to the LAB's networking equipment or settings.

---

### Post by Bleek_II on 2008-11-13
I found a way to do it.
[http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly](http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly)
Just in case anyone else needs to know.

---

