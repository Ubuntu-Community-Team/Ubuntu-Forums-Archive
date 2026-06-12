---
title: "Zonet ZEW2545 Wireless Adapter"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-11-03
I had to get a USB wireless adapter since HP can't build a laptop (I bought the lemon line of laptops where the GPU slowly fries the motherboard--the wireless was first to go). Anyway, it's the Zonet ZEW2545 and I can't get a driver for this thing.

I can't find an .inf to use with ndiswrapper, and there's not any posts I can find on how to get it to work with linux. I guess it's relatively new because it's wireless n capable. Is there a custom driver out there for linux or can I make use of .sys files somehow?

Thanks!

---

### Post by Leo_u on 2009-11-13
I have the xact same adapter, and the exact same problem ... please help

---

### Post by topviet on 2010-03-27
Zonet ZEW2546 uses Ralink RT3070 Chipset. I follow the suggestion from [http://ubuntuforums.org/showpost.php?p=8654774&postcount=8](http://ubuntuforums.org/showpost.php?p=8654774&postcount=8) to blacklist rt2800usb.

Open terminal to run this command
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
add this line at the end
```
 blacklist rt2800usb
```

It work on computer using Ubuntu 10.04 Lucid Lynx Beta 1.

---

### Post by jamestrowbridge on 2010-03-27
I can attest, the above fix worked for me, I restarted before plugging in the wireless just to make sure the new blacklist entry took effect:
Pentium 3 machine
Ubuntu 9.10 - Karmic Koala
USB, connected with 15 foot extension (to help pick up wireless signal around a brick apartment wall) - Zonet ZEW2545

By the way, thank you.... I've been struggling using a crossover cable between this machine and a Windows XP machine running the ZEW2545 and using network connection sharing, which is a huge pain when trying to use the Ubuntu as a test server over the Internet (extra firewalls, additional routers, additional port forwarding is now all eliminated).

Thanks again!

---

### Post by FresnoFightFan on 2010-07-26
i'm running 10.04 32bit  and i typed waht u guys said up there. it gives me a window with 

This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

am i missing something?

---

