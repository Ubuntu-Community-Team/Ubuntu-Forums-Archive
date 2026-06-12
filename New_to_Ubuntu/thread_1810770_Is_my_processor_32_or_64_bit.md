---
title: "Is my processor 32 or 64 bit?"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by aykoola on 2011-07-23
in terminal, i got this answer:

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               1200.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K


does it mean i am 32 or 64bit (or is it even possible to be both?)? does it matter which version of a distro i install?

Thank you!

---

### Post by aykoola on 2011-07-23
grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts



plus i ran this. Does this mean i should install 64-bit instead of 32??

please help :( 

thank you!

---

### Post by Tea4all on 2011-07-23
It looks like a 64-bit processor. If the 64-bit version of Ubuntu boots, then its a 64-bit processor. If not, well, there you go.:P

---

### Post by haqking on 2011-07-23
64 bit due to the lm flag which means long mode

---

### Post by aykoola on 2011-07-23
but the funny thing is, i have a 32bit version installed currently? should i do a 64 bit install? will it work better or what? :)

thank you!

---

### Post by CaptainMark on 2011-07-23
run the command ```
sudo lshw |grep width |head -n 1
```if you have more than 3.7gb of ram use 64 bits if you want to use all your available speed, if you have less than this or you only do non cpu intensive tasks i would run 32bit

---

### Post by haqking on 2011-07-23
> **aykoola said:**
> but the funny thing is, i have a 32bit version installed currently? should i do a 64 bit install? will it work better or what? :)

thank you!

32 bit works fine on 64 bit arch, use a 64 bit Live CD, it should work fine.

the lm flag  ( pbe nx [COLOR=Blue]lm[COLOR=Black]) means long mode or 64 bit.[/COLOR][/COLOR]

---

### Post by aykoola on 2011-07-23
sudo lshw |grep width
    width: 32 bits
          width: 64 bits
             width: 64 bits
             width: 64 bits
             width: 8 bits
             width: 8 bits
          width: 32 bits
             width: 64 bits
             width: 64 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 64 bits
             width: 32 bits
                width: 64 bits
             width: 32 bits
             width: 32 bits
                width: 64 bits
             width: 32 bits
             width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 64 bits



this? what does it mean :D

---

### Post by JASONFUSARO on 2011-07-23
> **aykoola said:**
> grep flags /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts



plus i ran this. Does this mean i should install 64-bit instead of 32??

please help :( 

thank you!


this is mine

```

flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts

```I have Vista 32 bit but I have installed all 64 bit Distros

there are a couple of diffs between yours and mine but it may work, give it a try

I just compiled the 64 bit 3.0 kernel version to and enable dual core with no problems

---

### Post by haqking on 2011-07-23
> **aykoola said:**
> sudo lshw |grep width
    width: 32 bits
          width: 64 bits
             width: 64 bits
             width: 64 bits
             width: 8 bits
             width: 8 bits
          width: 32 bits
             width: 64 bits
             width: 64 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 64 bits
             width: 32 bits
                width: 64 bits
             width: 32 bits
             width: 32 bits
                width: 64 bits
             width: 32 bits
             width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
                width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 64 bits



this? what does it mean :D


as already stated your cpu supports 64 bit operation, it has the lm flag set.

64 bit

---

### Post by JASONFUSARO on 2011-07-23
```


jason@UbuntuStudio64bit:~$ cat  /proc/cpuinfo


processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping    : 13
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 2925.88
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping    : 13
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 2925.86
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


```this will help to 

[http://bamajr.com/2011/02/02/kubuntu-how-to-tell-if-the-cpu-is-64-bit-capable/](http://bamajr.com/2011/02/02/kubuntu-how-to-tell-if-the-cpu-is-64-bit-capable/)


```

jason@UbuntuStudio64bit:~$ sudo lshw |grep width
    width: 64 bits
          width: 64 bits
             width: 64 bits
             width: 64 bits
          width: 32 bits
             width: 64 bits
             width: 64 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 64 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
                width: 64 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits
             width: 32 bits


```

---

### Post by aykoola on 2011-07-23
> **haqking said:**
> 32 bit works fine on 64 bit arch, use a 64 bit Live CD, it should work fine.

the lm flag  ( pbe nx [COLOR=Blue]lm[COLOR=Black]) means long mode or 64 bit.[/COLOR][/COLOR]

sorry haqking! i don't know how i managed to miss your post.

So, it owuld be wise to install a 64 bit version. thank you!

---

### Post by haqking on 2011-07-23
> **aykoola said:**
> sorry haqking! i don't know how i managed to miss your post.

So, it owuld be wise to install a 64 bit version. thank you!

sure...it would be wise to try a live cd but should work fine.

Nowadays if you have the architeture there is no real reason to not run 64 bit. there can be some issues with some apps etc but then thats the same for 32 bit.

enjoy

---

