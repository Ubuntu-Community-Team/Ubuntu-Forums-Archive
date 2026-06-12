---
title: "how do i find out if my computer is 32-bit or 64-bit?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by soni1770 on 2009-11-21
i tried asking it but it's being quite quiet now

---

### Post by NoaHall on 2009-11-21
uname -a

---

### Post by soni1770 on 2009-11-21
Linux soni 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


ummm...

---

### Post by lisati on 2009-11-21
The "i686" bit tells me that you are running a 32-bit OS, (which will run on a 64-bit computer)

Many modern computers are 64-bit capable.

(I'm just scratching my head to remember which command gives the CPU info rather than the OS, **cat /proc/cpuinfo** comes to mind)

---

### Post by soni1770 on 2009-11-21
soni@soni:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping    : 13
cpu MHz        : 1000.000
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
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3656.94
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping    : 13
cpu MHz        : 1000.000
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
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3657.50
clflush size    : 64
power management:




ohhhh!

---

### Post by lisati on 2009-11-21
I might be mistaken but that looks 64-bit to me.

---

### Post by soni1770 on 2009-11-21
yippi!!

might wait for the next ubuntu distro to change tho.
unless i get really bored

cheers!

---

### Post by lisati on 2009-11-21
I just looked up your CPU at [http://ark.intel.com/Product.aspx?id=32427](http://ark.intel.com/Product.aspx?id=32427) and it appears to support the 64-bit instruction set.

---

### Post by NoaHall on 2009-11-21
Oh, I see, you were asking how to find out if it's capable of 64 bit? The answer is yes.

---

### Post by soni1770 on 2009-11-21
double yes!

yesh!

thanks all:KS

---

### Post by peculiar penguin on 2009-11-21
All Core 2 branded processors are 64-bit, and the "lm" (long mode) flag is another hint.

---

