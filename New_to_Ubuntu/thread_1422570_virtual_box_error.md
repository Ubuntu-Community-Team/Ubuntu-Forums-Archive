---
title: "virtual box error"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by dagarshali on 2010-03-05
Hi,
I have Ubuntu karmic kaola 64 bit installed on my computer.. When i try to install a 64 bit windows via virtual box, i get the error saying it is a 32 bit computer. Could anybody help me here..

this the result of uname -a in ubuntu

Linux olivegarden 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

this /proc/cpuinfo

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips	: 4256.47
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips	: 4259.26
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:




Regards,
Vishwa

---

### Post by TurnOfTide on 2010-03-05
I can comment this:

I originally installed windows 7 64bit. I created a new, resized partion for karmic. I attempted to install the 64bit version of karmic (from boot) and got a disc read error. I tried to originally install this disc on both Virtual Box and VMware(from windows 7), only to see those attempts crash miserable, so clearly the disc OR my computer were bad. Rarely does a disc not burn correctly and moreover, it is impossible to burn a disc that gets corrupted yet still manages to boot. So I just opted for the 32 bit version, espicaially since 32bit versions of programs are way more stable than 64 bit. I had problems with using 64bit version of MySQL because the database drivers I used in Ruby were failing me. I Switched to the 32 bit version - viola.

My advice is to just stay with 32bit, you aren't going to gain a performance increase just because you run the 64 bit version of something anyway. Unless perhaps you are sitting on > 4 gigs ram and don't want waste them.

---

