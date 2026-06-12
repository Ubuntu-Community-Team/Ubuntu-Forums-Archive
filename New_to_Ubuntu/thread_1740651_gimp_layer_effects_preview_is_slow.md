---
title: "gimp layer effects preview is slow"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-27
I got layer effects for gimp but the preview is really slow. How to fix it?

---

### Post by clhsharky on 2011-04-27
RobikShrestha


How much memory does your computer have?



Sharky

---

### Post by techunit on 2011-04-27
Where did you get that cause I want it! You could just need more mem perhaps more swap.

---

### Post by josephmills on 2011-04-27
lets take a better look at your hardware to see if it is gimp or not. please press ctrl+alt+t when the terminal shows up please enter ```
free -m 
``` and paste that here also a ```
cat /proc/cpuinfo 
``` thanks

---

### Post by RobikShrestha on 2011-04-27
Sorry but I forgot where i got it from. Actually I have two of them. One in python and another in script-fu. Why don't u just google it, it was easy to find.

 free -m
             total       used       free     shared    buffers     cached
Mem:          2895        909       1986          0        116        417
-/+ buffers/cache:        375       2519
Swap:          723          0        723
suzuki@suzuki-laptop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
bogomips    : 4400.01
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
bogomips    : 4398.99
clflush size    : 64
power management:


I have 3 gb of memory. May be the algorithm of preview is slow??

---

