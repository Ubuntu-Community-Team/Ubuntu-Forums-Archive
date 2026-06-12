---
title: "No wired internet after upgrading to 8.04 (static IP)"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by drinu21 on 2008-06-16
Hi all, 

I have recently updated ubuntu to 8.04 and cannot get the internet working. i have an external dsl modem connected to the ethernet card without any routers, therefore i assigned the a static ip adress to the network card. now when running pppoeconf it doesn't find any "concentrators". 
than when i load the -14 kernel it just works fine, but with -18 it just isn't working

any ideas??

thanks 
adrian

---

### Post by W A L E E D on 2008-06-16
I am having this problem too!!
After I did upgrading to my Ubuntu 8.04 today, I am facing this problem.
I need to "Reload" a website more than 4 times to open it.
I hope if any body can help me with this problem.
Thank you.

---

### Post by Iowan on 2008-06-17
No guarantees - see if turning off "roaming profile" (or something similar) helps.

---

### Post by drinu21 on 2008-06-17
Roaming mode is not enabled. i cannot understand whats wrong, cause the 8.04 loaded with -14 kernel is working while when loading in with -18 is not working, leaving the same settings

---

### Post by drinu21 on 2008-06-18
There were some updates and installed them and now is working! :) i guess there was something with the kernel version -18, because now is updated to the -19

---

