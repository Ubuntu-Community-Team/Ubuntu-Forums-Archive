---
title: "NetworkManager issue"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by profeta81 on 2009-05-11
Hi

I have some problem with NetworkManager. Every now and again it begins running on 100% of my pc PCU and within 30 sec - 1 min it has filled all my memory and the PC freezes (in these occasions I can only power off the laptop). To keep using my PC I usually keep a terminal opened and whenever I see the pc slowing down without any reason, I kill it (sudo kill) before it fills the memory and restart it.

anybody can help? Let me know if you need more info about the problem and how I can get them.
Cheers

---

### Post by pro003 on 2009-05-11
what is the name of the process in sys monitor that is causing you problems?

---

### Post by kapi on 2009-05-11
don't know if this will help or not, but my memeory and speed went through the roof when I used to use Wine. Someone said it was quite common to get a memeory leak when using wine. It happened all the time so instead I installed virtual box and run what programs I need in there.

Like I said - don't know if it's related to your problem but that's the only similar problem to yours I've had so far.

---

### Post by profeta81 on 2009-05-11
> **pro003 said:**
> what is the name of the process in sys monitor that is causing you problems?

I don't know the name on Sys monitor... on top:

PID      USER         PR     NI    VIRT      RES      SHR S      %CPU   %MEM      TIME+      COMMAND 
***      root         20     0     283m      271m     2164 R     66     26.9      2:21.17    NetworkManager



btw, it seems like there's been other people with a similar memory leak problem, although the bug-fix seems to have been released...

and no, this has nothing to do with wine...

cheers

---

### Post by pro003 on 2009-05-11
the name is "nm-applet" 
check how much it uses , also check other processes as well, perhaps it's not network manager

---

