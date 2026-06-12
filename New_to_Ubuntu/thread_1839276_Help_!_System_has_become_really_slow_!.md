---
title: "Help ! System has become really slow !"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by blade4 on 2011-09-05
Hi all . Of late my system has gotten really slow . Boot takes almost five times longer now and the apps also take much longer to open . I didn't make any major changes to my system - just the usual updates and stuff . I have a feeling that this has something to do with my DMA settings . I thought about screwing around with my dma but hdparm -d says something about bad magic number in superblock - which the noob in me doesn't know what to make of . 

My system is Ubuntu 10.04.3 LTS on Wubi . Please help me out here guys . Thanks in advance .

---

### Post by jfreak_ on 2011-09-05
Taking a wild guess here
Install bootchart and restart, then check the bootchart log to see where the booting is getting slow.
For the slow opening problem, run 'top' in the terminal to see if any process is hogging memory
Good Luck

---

