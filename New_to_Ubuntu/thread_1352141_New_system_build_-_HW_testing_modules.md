---
title: "New system build - HW testing modules?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by mcm15901 on 2009-12-11
Hello folks - my first-ever post to these forums. I'm building a Pentium Dual-Core (Wolfdale) system on an ASUS motherboard with integrated Intel GMA X4500 graphics. I'm inclined to go with the 64-bit version of Ubuntu Studio, Karmic 9.10 ...
 
What kind of system testing, including memory burn-in, can I do right from the DVD even before I install an OS? Or is there a better Linux distro, like Knoppix maybe, for such initial tests?

---

### Post by LowSky on 2009-12-11
The regular Ubuntu Live CD has a memory test, but thats it.

Why do you need to do these tests?

---

### Post by mcm15901 on 2009-12-11
Well, I'm new to the Linux scene and it's been almost 10 years since I've built a system, so I want to know the available tools for examining the integrity of the new hardware I'm getting.

---

### Post by Keith_Beef on 2009-12-15
> **mcm15901 said:**
> Well, I'm new to the Linux scene and it's been almost 10 years since I've built a system, so I want to know the available tools for examining the integrity of the new hardware I'm getting.

Maybe you'd be better off with Ultimate Boot CD for doing memory and CPU testing before you install Ubuntu.

K.

---

### Post by MooPi on 2009-12-15
I have found Prime95 to be an excellent burn in tool. If your CPU isn't up to snuff, it will expose it. Can test memory and CPU in tandem. Another good tool is "glxgears" to stress your gpu. Prime95 is also good for testing stability in over clocked situations.
[http://mersenneforum.org/gimps/mprime259-linux64.tar.gz](http://mersenneforum.org/gimps/mprime259-linux64.tar.gz)

---

