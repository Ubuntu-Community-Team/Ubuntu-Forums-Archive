---
title: "need some help"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by belgaroin on 2011-02-11
i have ubuntu 10.10 on a laptop and i want to find out if the laptop is 32 or 64 bit .I know how to find it using windows but how to i find out using ubuntu? i mean to find out if its 32 or 64 bit processor.

---

### Post by The_Eggert on 2011-02-11
> **belgaroin said:**
> i have ubuntu 10.10 on a laptop and i want to find out if the laptop is 32 or 64 bit .I know how to find it using windows but how to i find out using ubuntu? i mean to find out if its 32 or 64 bit processor.

In a terminal, write:

```

cat /proc/cpuinfo | grep lm

```

If you get an output, it's a 64-bit processor - If not, it's a 32-bit :)

---

### Post by lisati on 2011-02-11
Most modern CPUs are 64-bit machines (citation needed). As for finding out, there are a number of possible answers, some of which will provide more useful information than others. For example, if you run this from the command line (from the Applications->Terminal menu option):
```
uname -a
```
This will tell you some information about which version of Ubuntu you are running, and provide a clue as to whether its 32-bit or 64-bit.

Another one:
```
cat /proc/cpuinfo
```
The "cpuinfo" will tell you some information about the CPU in your system. 

Feel free to ask if you need some help interpreting the output: if I'm not available (it's lunchtime here) someone else might be able to step in.

---

### Post by jerrrys on 2011-02-11
open a terminal and enter 
uname -m

---

### Post by belgaroin on 2011-02-11
came up as x86_64

---

### Post by belgaroin on 2011-02-11
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 4321.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 4322.49
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

got this from other command i typed in

---

### Post by The_Eggert on 2011-02-11
> **belgaroin said:**
> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 4321.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 4322.49
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

got this from other command i typed in

All I get from that, is what we already know - That you indeed have a 64-bit processor

---

### Post by The Cog on 2011-02-12
Using lisati's advice, I see that "lm" is one of the flags. I don't know what it means, but I believe him that it means it's a 64-bit CPU.

Note that uname -m isn't a sure-fire way to tell. uname -m on my system here says i686 which I think means a 32-bit CPU, but in fact I know it's a 64-bit CPU. uname tells you which version of OS, not which type of CPU.

---

### Post by robsoles on 2011-02-12
> **The Cog said:**
> Using lisati's advice, I see that "lm" is one of the flags. I don't know what it means, but I believe him that it means it's a 64-bit CPU.

Note that uname -m isn't a sure-fire way to tell. uname -m on my system here says i686 which I think means a 32-bit CPU, but in fact I know it's a 64-bit CPU. uname tells you which version of OS, not which type of CPU.


To the best of my understanding the i686 architecture is much more akin with x86_64 than with i386.



I love lisati's "(citation needed)" there above, classic stuff - wiki much, Richard? :lol:

---

### Post by cascade9 on 2011-02-12
> **robsoles said:**
> To the best of my understanding the i686 architecture is much more akin with x86_64 than with i386.

i386 is 32bit, i686 is 32bit. i686 is closer in time to x86-64 than i386, but aside from that it would be debatable if i686 is closer to x86-64 or i386. Id' say that i386 is closer, i386 might actually have a chance of executing i686 instructions.

---

### Post by robsoles on 2011-02-12
> **cascade9 said:**
> i386 is 32bit, i686 is 32bit. i686 is closer in time to x86-64 than i386, but aside from that it would be debatable if i686 is closer to x86-64 or i386. Id' say that i386 is closer, i386 might actually have a chance of executing i686 instructions.

Just proof to me that I shouldn't ever rely on my memory of stuff **without** verifying it via Google or some other wealth of information - could have sworn I've installed a 64 bit OS on an actual i686 but apparently it would be one of the times that booting from the installation media would have reported that I needed 32 bit installation media instead :roll:

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

---

### Post by cascade9 on 2011-02-13
> **robsoles said:**
> Just proof to me that I shouldn't ever rely on my memory of stuff **without** verifying it via Google or some other wealth of information - could have sworn I've installed a 64 bit OS on an actual i686 but apparently it would be one of the times that booting from the installation media would have reported that I needed 32 bit installation media instead :roll:

If you had a 64bit machine and installed 32bit on it, then used uname it would report as i686. ;)

---

