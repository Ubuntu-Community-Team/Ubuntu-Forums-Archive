---
title: "32 bit or 64bit"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by bac0926 on 2010-10-21
I had my computer custom built but that co. has gone out of business. Some one told me that I am running Ubuntu 32 bit but that my system is 64 bit. How can I tell if my hardware is 64 bit or 32 bit. I am running Ubuntu 10.10

---

### Post by LowSky on 2010-10-21
in teminal use this command, it will list your PC's processor
```
dmesg | grep cpu
```

paste the info here if you need help determining the model

32 or 64bit is fine to use, 64 bit will work on most computer made in the last 5 years with a few exceptions.

---

### Post by mikewhatever on 2010-10-21
Don't worry about it. 64bit is meaningless for most home users, and the more you listen to zealots trying to get you do things, the more confused you'll get.

---

### Post by BikeHelmet on 2010-10-21
That command didn't spit out anything useful on my box.

If it doesn't for you either, try this one:
```
sudo lshw -c cpu
```
```
  *-cpu                   
       description: CPU
       product: VIA Eden Processor 1200MHz
       vendor: CentaurHauls
       physical id: 4
       bus info: cpu@0
       version: 6.13.0
       slot: Socket 370
       size: 1200MHz
       capacity: 1200MHz
       width: 32 bits
       clock: 100MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en cpufreq
```
x86-64 extension indicates 64bit support, right? :) 

This i686 VIA C7 lacks it.

---

### Post by perspectoff on 2010-10-21
> **mikewhatever said:**
> Don't worry about it. 64bit is meaningless for most home users, and the more you listen to zealots trying to get you do things, the more confused you'll get.

Meaningless or not, it sure is a lot faster (at least in Linux, if not in Windows)!

---

### Post by eze1969 on 2010-10-21
I tried the 64-bit version of 10.04 and couldn't get Java or Flash to work. From what I could tell from reading these forums the support for 64 bit is a bit lacking :(
I have an I3, 4G RAM...32 bit 10.10 runs like a scalded dawg with all the pretty Compiz effects :D I'm not sure how much faster the 64 bit version could offer but until the support gets better, I'll stick to 32 bit...happily!

---

### Post by perspectoff on 2010-10-21
> **eze1969 said:**
> I tried the 64-bit version of 10.04 and couldn't get Java or Flash to work. From what I could tell from reading these forums the support for 64 bit is a bit lacking :(
I have an I3, 4G RAM...32 bit 10.10 runs like a scalded dawg with all the pretty Compiz effects :D I'm not sure how much faster the 64 bit version could offer but until the support gets better, I'll stick to 32 bit...happily!

Maybe I'm missing something. I hadn't noticed Java not working. Perhaps I'm not using Java hard enough...

Besides, don't 32-bit apps work with ia32libs? I know my 32-bit Skype works in my 64-bit system that way...

---

### Post by mikewhatever on 2010-10-21
> **perspectoff said:**
> Meaningless or not, it sure is a lot faster (at least in Linux, if not in Windows)!

Wasn't any faster for me.

---

