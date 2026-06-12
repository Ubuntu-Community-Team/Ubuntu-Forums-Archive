---
title: "Slow LAN Speeds"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by nuclearpidgeon on 2007-05-11
Hi,

Today I was transferring some files from my Ubuntu PC to my local XP PC (well call it OLDXP for no confusion), and the speed was HORRENDOUS!
I have never seen such a slow transfer rate. it took at least 5 minutes to copy a 5mb file!
Now my Ubuntu PC is dual-booted with XP (ill call it NEWXP). When I use NEWXP, I can transfer file to OLDXP at the full 100mbps. The files I was copying were on the NEWXP HDD, copied vis Ubuntu. The HDD is SataII so the speed shouldn't be a problem. (I removed a silly jumper limiting the speed to half!) But when I transfer files from the Ubuntu Partition, same speed.
My suspicion is that there is a setting (in Samba maybe) limiting the speed.

---

### Post by mfdc1969 on 2007-09-15
Yes, I have the same problem - when copying my personal files from XP to my server the time is about 1 hour 15 minutes.

When copying my same files from ubuntu to the server the time is double.

My server is running Samba - should I use something different instead of connecting to the Samba? (Note: Samba is required for other family to access file server).

Any suggestions ...

Mike

---

### Post by mfdc1969 on 2007-10-02
Update on my issues of slow LAN speeds:

- diabled server internal NIC and replaced with with 10/100/1000
- swithced to ssh connection
- assigned Static IPs in my D-Link Router

Life is much faster!

Thansk to all other forums for your great help!

M.

---

