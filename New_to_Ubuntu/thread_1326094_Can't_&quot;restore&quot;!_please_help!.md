---
title: "Can't &quot;restore&quot;! please help!"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by mydisguise09 on 2009-11-14
when I start up my Everex Cloudbook, at some point you can press 'Esc' and it lists the kernels:
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04.3 LTS, memtest86+

well before it used to have this thing at the end of the list that restores or whatever but it's not there (I upgraded/updated twice since the last time I saw this restore thing at the end of the list). I must have messed something up or messed around with something with Network Proxy or DNS or whatever because I can't get on the internet or I have to click on the wireless network in order for it to work. I want to restore my netbook but like I said earlier that restore thing in the list when you press 'Esc' isn't there! how can I fix connecting to the internet properly or restore my netbook? thanks for your help :D

---

### Post by jnorthr on 2009-11-14
1. save all your valuable data just in case.
2. if wireless was working sounds like it would be easier just to make the wireless work than do a complete re-install cos that may just put off having to solve the network issue till then and you might waste alot of time,
3. avoid a re-install if you can, but if you MUST, would suggest the 9.04 LTS version as it's networking seemed to work much better out of the box than 9.10.
4. can you find and run a terminal ? if so, try these commands to see whats up :

ifconfig
iwconfig
dmesg

you may need to do a man on these to see how/why they work.

---

