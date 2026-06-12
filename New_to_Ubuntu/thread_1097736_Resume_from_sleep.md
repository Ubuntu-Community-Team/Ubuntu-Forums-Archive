---
title: "Resume from sleep"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by marcus_c on 2009-03-16
Hi everyone,

I've just installed Intrepid Ibex 8.10 on my PC last weekend and it mostly works very nicely!!

There is one feature that doesn't appear to work and that is resuming from sleep/suspend. It suspends nicely (I have Suspend-to-RAM enabled in the BIOS) but when I try to resume, the machine powers up and the monitor comes out of standby, but the screen is blank. I'm forced to power cycle the PC and reboot to get back into Ubuntu. My PC will suspend and resume successfully with WinXP.

I have a Winfast system board with a NForce3 chipset. The graphics card is a XFXForce Nidia 6200(512MB). 

I've tried searching/googling for a fix and it seems a lot of people with all kinds of laptops/desktops have experienced this fault. Is there a known fix or is there going to be a fix in forthcoming ubuntu versions?

Hardly the end of the world I know, but it would be nice to get it working!

Any responses much appreciated!

---

### Post by jbrown96 on 2009-03-16
It should be a fairly easy fix, although I have problems with the newer graphics drivers. Make sure you use the drivers from System===>Administration===>Hardware Drivers and then follow these directions. [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

I can't remember the specific version but use the 177.xx one. The 180.xx series available from Nvidia website has caused some problems for me, but I haven't tried to fix it beyond following those directions.

---

### Post by marcus_c on 2009-03-17
Thank-you very much. I followed the instructions and sleep/resume now works. The only problem left is getting my wireless card to re-connect to my router after a resume, but thanks again!:D

---

### Post by jbrown96 on 2009-03-17
> **marcus_c said:**
> Thank-you very much. I followed the instructions and sleep/resume now works. The only problem left is getting my wireless card to re-connect to my router after a resume, but thanks again!:D

What do you mean it won't reconnect? I can help you get it working. Usually you just need to unload the module. Post the output of the following commands BEFORE and AFTER you suspend
```
lsmod
``` ```
ifconfig
``` 

Then also ```
lspci | grep Network
``` either before or after it doesn't matter.

---

### Post by sleepyjon on 2009-03-17
> **marcus_c said:**
> Thank-you very much. I followed the instructions and sleep/resume now works. The only problem left is getting my wireless card to re-connect to my router after a resume, but thanks again!:D

I occasionaly have a problem connecting to networks with my wireless card after suspend as well. I've found that disabling the card right before suspending the laptop then enabling it after coming out solves the issue.

Hope that helps some.

---

### Post by jbrown96 on 2009-03-17
> **sleepyjon said:**
> I occasionaly have a problem connecting to networks with my wireless card after suspend as well. I've found that disabling the card right before suspending the laptop then enabling it after coming out solves the issue.

Hope that helps some.

That's what I was thinking, but it should be easy to add that to the sleep script, so it happens automatically.

---

