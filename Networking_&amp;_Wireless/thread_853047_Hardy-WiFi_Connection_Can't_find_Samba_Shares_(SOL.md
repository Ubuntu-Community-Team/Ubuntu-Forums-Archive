---
title: "Hardy-WiFi Connection: Can't find Samba Shares (SOLVED)"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by pmbucalo on 2008-07-08
Like many others, I have found that using the wireless connection on my laptop to connect to my Samba server impossible, though I can connect through a UTP cable connection. The culprit is Samba -- loaded on the laptop by default after installation. I have no reason or desire to share directories from my laptop, so the quick fix was to remove Samba from my init runlevel list:

$ sudo sysv-rc-conf --level 2 samba off

then shutdown Samba:

$ sudo /etc/init.d/samba stop

a check can be made by running ps:

$ ps -e

Now using only my wireless connection my laptop will find and mount my server shares in Nautilus or through pyNeighborhood. I'm happy again.

---

