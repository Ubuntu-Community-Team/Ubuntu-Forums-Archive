---
title: "Make space on pendrive linux"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by BilleeSugger on 2010-12-16
I have just installed Ubuntu 10.10 on a pendrive . I downloaded the updates but it failed to install all as it ran out of space , I uses persistance so thought it would be OK . How do I free up space ? 
Step by step pls

---

### Post by Wobblybob on 2010-12-18
The obvious thing is to make sure yo have deleted the files in the waste bin shut down and restarted again.

Another option you could try is removing the cache of program packages left after you have installed programs by opening a Terminal and typing;

sudo rm -rf /var/cache/apt/*

this r will mean that if you want to reinstall any of these programs again the system will have to download them off the net again rather than from the cache.

---

### Post by BilleeSugger on 2010-12-19
Thanks but I used a bigger drive now , works fine.

---

### Post by Wobblybob on 2010-12-19
:p that's a better option, please mark this thread as solved.

---

