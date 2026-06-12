---
title: "[SOLVED] Does broadcom wireless work in intrepid?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ubudog on 2009-01-06
Hi.  I don't have Intrepid but I have a broadcom wireless card and it took a hell of a time to get it working.  I was wandering if it works in Intrepid because I was thinking about upgrading (I currently have 8.04).  If anyone knows please let me know.







Thanks

---

### Post by nhasian on 2009-01-06
i believe broadcom makes many different chipsets, but i installed ubuntu 8.10 on a new HP laptop and it had a broadcom wifi adaptor and it worked fine.  you can see exactly which one you have by running in a terminal:

```
lshw -C network
```

---

### Post by JoshuaRL on 2009-01-06
I have Broadcom wireless.  Not sure what chipset (I'm not at it at the second and I can't find the specs online for my laptop) but Hardware Drivers detected it and offered the proprietary drivers for me to install.  Everything works great, even the disable button.  

I'll be honest, when it just worked out of the box I was pretty excited.  I began to rub my friend's noses in it.  Yeah.

---

### Post by ugm6hr on 2009-01-06
Why not try the Intrepid LiveCD to check if your works?

My new Dell Mini 9 has an internal "USB" Broadcom 4310, which appears to work fine in both Hardy and Intrepid.

---

### Post by igknighted on 2009-01-06
Some work great with the new wl driver, but some are the same old b43 which works, but not quite as well as some others (like intel, or the wl driver).  If you run 'lspci' you can see which chip you have, and which driver would be used.

---

### Post by ubudog on 2009-01-06
Thanks Everyone. That solves my problem.

---

