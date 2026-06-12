---
title: "32-bit vs 64-bit - for a workstation ..."
date: 2009-07-23
forum: New to Ubuntu
---

### Post by cwmoser on 2009-07-23
What are your perceptions of the the 32-bit version versus the 64-bit version of Ubuntu 9.04 Jaunty?

I moved from the 32-bit 8.04 Ubuntu to the 64-bit 9.04 Ubuntu and have noted some unusual issues with 64-bit Jaunty - i.e. pauses (tried the latest nVidia drivers, just turned Compiz off), FireFox issues (have to create another profile), USB devices would not mount (have to reboot), etc.

Have not tried 32-bit Jaunty - so I was wondering what are your perceptions?

Thanks

Carl

---

### Post by wizard10000 on 2009-07-23
Clean install of 64-bit Jaunty has worked pretty well for me.  Can't say I've experienced any of the issues you mention.

---

### Post by regala on 2009-07-23
> **cwmoser said:**
> What are your perceptions of the the 32-bit version versus the 64-bit version of Ubuntu 9.04 Jaunty?

I moved from the 32-bit 8.04 Ubuntu to the 64-bit 9.04 Ubuntu and have noted some unusual issues with 64-bit Jaunty - i.e. pauses (tried the latest nVidia drivers, just turned Compiz off)


this is due to a closed source driver, you can't say it is because you run 64 bits. And you compare between DIFFERENT versions of Ubuntu, which makes the comparison quite irrelevant: not the same kernel, not the same userland... the issues can come from running 64 bits but I sincerely doubt it, I never encountered an issue, or should I say, besides the issues that can come from running the 32-bits emulated mode on a 64 bits architecture. :)

> FireFox issues (have to create another profile)

again, it is not relevant, Mozilla Foundation already stressed enough the fact that profiles must be backed up between major versions of Firefox and that issues can (and will on cases) appear.

> USB devices would not mount (have to reboot), etc.

I don't understand the problem, what do you do when you have to mount a USB stick ?

> 
Have not tried 32-bit Jaunty - so I was wondering what are your perceptions?


On a 64 bits architecture, 32 bits software have always been good, but since a few years now, 64 bits have always well behaved except for the few cases where the problem was the lack of 64 bits proprietary software (gaps that are now filled) and more importantly, it has always been faster and better. Anyway, you can't compare 2 versions with 2 release cycles between them seriously. You can only compare the 2 architectures on the same software.

best regards,

---

### Post by reeseslover531 on 2009-07-23
pretty much if you have 4gb or more of ram, 64-bit otherwise no reason for 64-bit.

---

### Post by powel212 on 2009-07-23
+1> pretty much if you have 4gb or more of ram, 64-bit otherwise no reason for 64-bit.

They both work great but if you have less than 4G RAM you won't notice a difference and if you do use 64Bit you will have to to a little forum searching to get a few applications working under 64Bit. But in the end 64Bit is awesome. 
I run 64Bit Jaunty on my main box with 8G RAM and use the RAM overhead for my virtualbox guests. 1,2,3,4 OSs running at once on 3 monitors. Try that in windows. haha

Powel

---

### Post by XCan on 2009-07-23
64-bit all the way. I use it both on my workstation (12 GB RAM) and my home desktop (4 GB RAM). Only issues I've encountered was that the 32-bit flash plugin sucked, however, ever since Adobe's 64-bit plugin all have been great!

---

### Post by regala on 2009-07-23
> **reeseslover531 said:**
> pretty much if you have 4gb or more of ram, 64-bit otherwise no reason for 64-bit.

no there's always a reason not to run the EMULATED 32 bits mode, because 32-bits mode on a 64-bits architecture means a loss of ~30% perf.
no reason to go 32 bits now that flash et.al. support x86_64.

---

### Post by jerome1232 on 2009-07-23
Actually running 32 apps on a 64 bit OS has zero to very little slow down in performance as compared to running it on a 32 bit OS.

Unlike IA-64, x86_64 doesn't have a performance penalty for running 32 bit code.

>     The architecture's intended primary mode of operation; it is a combination of the processor's native 64-bit mode and a combined 32-bit and 16-bit compatibility mode. It is used by 64-bit operating systems. Under a 64-bit operating system, 64-bit, 32-bit and 16-bit (or 80286) protected mode applications may be run.

    Since the basic instruction set is the same, there is almost no performance penalty for executing x86 code. This is unlike Intel's IA-64, where differences in the underlying ISA means that running 32-bit code must be done either in emulation of x86 (making the process slower) or with a dedicated x86 core. However, on the x64 platform, 32-bit x86 applications may still benefit from a 64-bit recompile, due to the additional registers in 64-bit code, which a compiler can use for optimization. 

edit: So in other words by running 64 bit you may be making more difficult to install a few select proprietary apps. By running 32 bit you may be sacrificing speed on cpu intensive operations.

---

### Post by Sef on 2009-07-23
> +1 	Quote:
 	 	 		 			 				pretty much if you have 4gb or more of ram, 64-bit otherwise no reason for 64-bit. 			 		 	 	 
They both work great but if you have less than 4G RAM you won't notice a difference

Depends on what you do.  If you use apps that use a lot of CPU, e.g., video editing, gaming or transfer lots of photos to your computer or usb key, then it can make a big difference. If not, not much then.

---

