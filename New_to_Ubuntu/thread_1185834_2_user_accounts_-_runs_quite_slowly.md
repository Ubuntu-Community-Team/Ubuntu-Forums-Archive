---
title: "2 user accounts - runs quite slowly"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-06-12
I have set up on my machine 2 accounts - a home one (being the primary one) and a work one. The home one has not seen any degradation in speed etc but when I switch used to the work account, it seems to run quite slowly...and some times it just hangs when I switch user.

What am I doing wrong?

---

### Post by Sinkingships7 on 2009-06-12
Could it be that you're switching users? If you just switch, then you have both logged in at the same time, combining the processes from each. While this shouldn't really be too much of an issue, you should try logging off your Home account and logging in to ONLY your Work account to see if there's a difference. Also, if you have Compiz running, try disabling it.

---

### Post by dunbrokin on 2009-06-12
Agreed, if I log out and log back in there will not be an issue....I just thought that switching should not have caused such a problem and wondered if there was a way around it other than logging off.

---

### Post by Sinkingships7 on 2009-06-12
> **dunbrokin said:**
> Agreed, if I log out and log back in there will not be an issue....I just thought that switching should not have caused such a problem and wondered if there was a way around it other than logging off.

Unfortunately not, if you're running lower-end hardware. May I ask for your specs?

On that note, it may be beneficial to switch to a lighter weight distro, like Xubuntu.

---

### Post by dunbrokin on 2009-06-12
Computer
Processor	2x Intel(R) Core(TM)2 Duo CPU P9400 @ 2.40GHz
Memory	3566MB (1008MB used)
Operating System	Ubuntu 9.04

---

### Post by Sinkingships7 on 2009-06-12
> **dunbrokin said:**
> Computer
Processor	2x Intel(R) Core(TM)2 Duo CPU P9400 @ 2.40GHz
Memory	3566MB (1008MB used)
Operating System	Ubuntu 9.04

Wow. That's unexpected. After careful consideration, I have decided that I have no clue what's wrong. Your specs should be running Ubuntu just fine, even with multiple people logged in at once. 

What about Compiz? Any diagnostic on that?

---

### Post by dunbrokin on 2009-06-12
How do I check Compiz....I do have it enabled....I also notice that Cheese Webcam Booth runs slow on video mode...if that is any help?

---

### Post by Sinkingships7 on 2009-06-12
> **dunbrokin said:**
> How do I check Compiz....I do have it enabled....I also notice that Cheese Webcam Booth runs slow on video mode...if that is any help?

Based on this, I want to say Compiz is at fault. Only one way to check. Right click your desktop, go to (I believe) Customize desktop background, and go to the Visual Effects tab on the far right. Choose None. Now try switching to see if the problem persists.

---

### Post by dunbrokin on 2009-06-12
OK, tried that with Cheese Booth (and I turned off Cairo Dock also...) but made no real difference.....still very choppy video and sound.

On the work account, Firefox is soooooooo slllllooooooowwwwwwwwww.....

---

### Post by nandemonai on 2009-06-12
What video card / drivers?

In terminal:

```
lspci | grep VGA
```

And..

```
lshw
```

Look for the display section. Product and module would be handy. ;)

---

### Post by dunbrokin on 2009-06-12
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
~$ lshw
WARNING: you should run this program as super-user.
            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3482MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     P9400  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0

---

### Post by Hobgoblin on 2009-06-12
> **dunbrokin said:**
> ~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


I was about to suggest it would be Intel video.

Have a search for Intel video issues with Jaunty, there are some known issues and possible fixes.

---

### Post by dunbrokin on 2009-06-13
OK, thanks to all....

---

