---
title: "ndis enabled wlan card &quot;working&quot;, but can't get it to actually see the network"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by jdix123 on 2008-01-04
I've been following multiple threads to get my wireless NIC working through ndiswrapper.  According to all of those posts, it is :working:, that is my system recognizes it and the driver is supposedly good.

But I can't get it to actually work on my network.

I tried to configure it through the terminal following the thread <a href="http://ubuntuforums.org/showthread.php?t=31926">here.</a>  It did actually say the name of my network, that it could "see" it.  But when I tried to configure it through Gnome's Network tool I couldn't get it to work.

Ubuntu 7.1

---

### Post by Teronap on 2008-01-05
Just a few questions that are needed to fix this problem
What encryption do you have?
What card is it?
what is the output of ```
 sudo ndiswrapper -l
```?

---

### Post by jdix123 on 2008-01-07
i386 (I think is what you're asking for by "encryption")
Its a D-Link WUA-1340


sudo ndiswrapper -l

Installed ndis drivers:
dr71wu             driver present, hardware present






Sorry, I don't know how to get that code box...

---

