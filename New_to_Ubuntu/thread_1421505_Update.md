---
title: "Update"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-03-04
Hi,
 
I received and installed updates this morning and it seems I have some new Kernal options . One of them  simply did not work an sent me into a reboot loop . when I tried
the next it worked fine. This was after the recomended restart . Just curious why this happened ?

---

### Post by kanikilu on 2010-03-04
Sorry this doesn't help, but I walked away during my updates and reboot and as I got back, I saw some text flash on the screen and then it rebooted and started fine. So I get the impression that it also got stuck in a loop, at least for a minute. Strange...:confused:

---

### Post by wojox on 2010-03-04
When you tried the next reboot or previous kernel?

---

### Post by kanikilu on 2010-03-04
For me, the new one booted eventually, and from what I gather, same with the OP (sorry, don't mean to hijack the thread ;) )

```
$ dpkg -s linux-image-generic
...
Version: 2.6.31.20.33
```

```
$ uname -a
Linux cepat 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
```

---

### Post by wojox on 2010-03-04
Probably just a quirky video driver.

---

### Post by kanikilu on 2010-03-04
I'm just curious to know what that text was that flashed across the screen before I had a chance to read it. Anyone know if that might be logged, and if so, where? I've browsed through a few of the logs in the System Log Viewer, but haven't come across anything yet that looks relevant.

// note to self: don't leave computer while doing kernel updates :p

---

### Post by Frogs Hair on 2010-03-04
I think the video driver is the best answer. When I installed Ubuntu 9 days ago I had minor problems 
until I updated the nvidia driver . If it doesn't like that kernel  I will use the other.

                                                                                                           Thanks

---

### Post by Frogs Hair on 2010-03-04
> **wojox said:**
> When you tried the next reboot or previous kernel?
The new Kernel doesn't work.

---

