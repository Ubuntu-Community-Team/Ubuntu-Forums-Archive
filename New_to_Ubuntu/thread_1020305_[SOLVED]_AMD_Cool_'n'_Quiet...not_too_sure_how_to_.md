---
title: "[SOLVED] AMD Cool 'n' Quiet...not too sure how to enable."
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Adamantus on 2008-12-24
Okay, I've been trying this for awhile now and everything that I've found online doesn't seem to work. It's mostly because my computer keeps telling me that it doesn't support CPU Frequency Scaling, yet I know it does. I'm running an HP dv5-1004nr on an AMD 64 Turion X2 processor. I know it supports CPU scaling because it was I used AMD's Cool 'n' Quiet technology with Vista. Now, I'm trying to use powernowd (I guess that's the linux module for CPU frequency scaling), but nothing seems to work. Where should I start? How can I enable CPU frequency scaling?

Also, I've been told Cool 'n' Quiet needs to be enabled in the BIOS, but my HP doesn't give me the option. The closest thing I could find was the "Fan Always On" option, but I'm pretty sure that's not it. My computer has been running pretty loudly and quite hot, even though most of the time I'm only using about 10% of my CPU's power, so I really wanted to try out powernowd/Cool 'n' Quiet.

Edit: It seems that the directory that most people deal with while using powernow (/sys/devices/system/cpu/cpu0/cpufreq/) doesn't even exist for me. I'm guessing that could be a problem.

---

### Post by Xiong Chiamiov on 2008-12-24
I have a Cool 'n' Quiet processor, and I enabled it in my BIOS.  I built it, though, so my BIOS is much less sucky than most of those that come in prebuilts.  Check and see if HP has a BIOS update?

---

### Post by 73ckn797 on 2008-12-24
> **Adamantus said:**
> Also, I've been told Cool 'n' Quiet needs to be enabled in the BIOS, but my HP doesn't give me the option. 

I have an AMD mobo and can set Cool & Quiet from the BIOS. It sounds like HP changed that. My board was separately purchased for a self built system. I have not looked into control from within Ubuntu. The fan runs quietly unless disk/processing activity increases. Then the fan kicks into high gear for several seconds or until the initial load subsides.

---

### Post by Adamantus on 2008-12-24
They do, but the site says it is only for Windows and that they don't have support for other operating systems right now.

And my output for cpufreq-info is:

cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

The guy in this thread seems to have a similar problem:
[http://ubuntuforums.org/showthread.php?t=1000132](http://ubuntuforums.org/showthread.php?t=1000132)

---

### Post by Titan8990 on 2008-12-24
Last I configured a kernel I saw options for Intel Speedstep but none for the AMD variant. May not be supported by the Linux kernel.

---

### Post by Xiong Chiamiov on 2008-12-24
Have you tried all the things listed in that thread?  By post 19, he recompiled his kernel, and that seemed to solve the issue.

---

### Post by Adamantus on 2008-12-24
I don't really know enough to recompile the kernel. I pretty much just started using linux and a lot of the lingo I read in that thread just left me lost.

---

### Post by Adamantus on 2008-12-24
Wow, I just found the solution here:

[http://xlife.zuavra.net/index.php/70/]("http://xlife.zuavra.net/index.php/70/")

It was really helpful. It didn't seem to have any other information that I hadn't seen before, but I tried it and it worked. Anyway, thanks to everyone. In case anyone sees that, the tutorial that guy gives is really straightforward and good for any beginners.

---

### Post by Cope57 on 2008-12-24
:mrgreen:

---

### Post by Adamantus on 2008-12-24
And just to add a little:

In order to make sure CPU Frequency Scaling starts up when you start the computer, you have to add the modules to /ect/modules.

If you mix that above link with this link [http://changelog.complete.org/archives/572-saving-power-with-cpu-frequency-scaling]("http://changelog.complete.org/archives/572-saving-power-with-cpu-frequency-scaling"), it's going to work.

So far, my computer seems to be 10x quiet and cooler and the battery life is twice as long...I love it.

---

