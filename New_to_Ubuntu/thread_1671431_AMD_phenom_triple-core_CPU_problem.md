---
title: "AMD phenom triple-core CPU problem"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by dsp_relax on 2011-01-20
Hi,

      My system is very slow because it use only 1 CPU instead of the 3  CPU on Ubuntu 10.10 (64 bit) machine. I searched the problem but didn't get any way to resolve it. Here i  am giving you my systems configuration details, please help me to solve  this.

_System Configuration :_
[B]
AMD Phenom
Triple-Core Processor
2.1 GHz
1 GB RAM
160 HDD
M2N MX-SE pluse
Operating System : Ubuntu 10.10 (64 bit)
[/B]


Thanks.
Deepak.

---

### Post by plucky on 2011-01-20
Welcome to the Forum

Open a terminal **(Applications > Accessories > Terminal)** and post output of ```
uname -a
cat /proc/cpuinfo
```

---

### Post by dsp_relax on 2011-01-20
Hi,

Here is the Terminal output :

**deepak@deepak-desktop:~$ uname -a**
Linux deepak-desktop 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:21 UTC 2011 x86_64 GNU/Linux

**deepak@deepak-desktop:~$ cat /proc/cpuinfo**
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 8450 Triple-Core Processor
stepping    : 3
cpu MHz        : 2109.611
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc up rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs npt lbrv svm_lock
bogomips    : 4219.21
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



Is anything you need let me know.

Thanks.

---

### Post by plucky on 2011-01-20
> Linux deepak-desktop 2.6.35-25-generic #43-Ubuntu SMP Thu Jan 6 22:25:21 UTC 2011 x86_64 GNU/Linux


Did you install a different kernel?

My Maverick install shows > Linux maverick-vm 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

Can you boot into a previous kernel from the grub menu?

Do you have the "Backports Repository" enabled?

Is it the same if you boot the Live Cd?

---

### Post by khelben1979 on 2011-01-22
As Plucky have mentioned in this thread, you need an [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing") linux kernel so that more than 1 cpu core can be used by your Ubuntu system.

---

