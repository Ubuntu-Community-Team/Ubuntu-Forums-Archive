---
title: "running dual network connections"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by rusty_nail on 2008-06-18
hey guys, 
i am wondering if it is possible to run both a wired and wireless connection at the csame time on ubuntu?
i am currently using gutsy, and i have an xbox which i would like to connect to my PC by wired connection then connect my PC to the internet. does anyone know a way to run both connections at the same time? 
so far as i have tried you can only run one at a time 
any help would be really appreciated. cheers

---

### Post by IOWAHC on 2008-06-18
AFAIK it should be possible.

With the Network Manager, I can't figure out how,
but if you drop to the console and configure each device yourself and set the IP Routes, then it should work.

But be carefull, you need two different IP - Ranges on the Devices, otherwise the routing would screw everything up.

cu

---

