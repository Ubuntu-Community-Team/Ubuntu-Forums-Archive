---
title: "ZyXEL AG-220 - how do i get it to work"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by voltorben on 2007-09-03
I have a ZyXEL AG-220 wireless USB adapter, but i can't get it to work... 
I've read that you should be able to get it to work with something called "zd1211rw", but i just can't figure it out... Could someone give me some help? :)
Im using Ubuntu 7.0 - the Feisty Fawn if it helps.

Thanks, Andy

PS: when i plug it in my USB port, the blue light on it is on.

---

### Post by voltorben on 2007-09-04
Today i tried a little with ndiwrapper, and installed the drivers, and it can see that its present:

andy@ubuntu:~$ ndiswrapper -l
wlanagg : driver installed
        device (0586:3412) present

(and when i plug it out, it can't see the device, which i presume is good)

But when i go to System>Administration>Network there is no wireless option... ?

---

