---
title: "the system hangs temporary  when the cpu is busy filling the swap !"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by amime on 2010-09-20
<<Temporarily >>
sorry for the weak language skills 
----------------------------------------------------------------------------------
I am running ubuntu 10.04

> 
uname -a 
Linux ****** 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
writing large amounts of data to the swap partition  causes  the system 
to hang for a while and struggle until i reboot it ...

actually , that happens when there is a non-responding process   hugging most of  system resources  in the background ... 

is there any other solution beside rebooting ... 

p.s. killing that specific non-responding process will retrieve  the system functionality a little but not totally ... 

thanks buddies

---

### Post by LowSky on 2010-09-20
we need a bunch more info on what is going wrong

What program/process is causing the lock-up
Can you please list your computer's hardware? How much RAM specifically would be great.

---

### Post by amime on 2010-09-20
> **LowSky said:**
> we need a bunch more info on what is going wrong

What program/process is causing the lock-up
Can you please list your computer's hardware? How much RAM specifically would be great.

CPU :  intel core2duo 2 GHz 
Ram : 2 GB DDR 
swap : /dev/sda10 which is a hard disk partition (700 MB ) , but i switch it off with :
> 
[I][U] sudo swapoff /dev/sda10  
[/U][/I]and then switch on  a formatted  usb mobile disk (4GB ) as LinuxSwap  with :
> 
*_ sudo swapon /dev/sdb1 _*
processes usually cause the problem :
mplayer  
VirtualBox 
firefox
Gnome-do 
..... 
the system and all of application are up to date .  





> 
*_cat /proc/cpuinfo _*

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3990.00
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3990.07
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

> 
[U][I]cat /proc/meminfo

[/I][/U]MemTotal:        2052392 kB
MemFree:          148792 kB
Buffers:          313720 kB
Cached:           827316 kB
SwapCached:            0 kB
Active:          1059708 kB
Inactive:         705720 kB
Active(anon):     495688 kB
Inactive(anon):   214400 kB
Active(file):     564020 kB
Inactive(file):   491320 kB
Unevictable:          48 kB
Mlocked:              48 kB
HighTotal:       1178440 kB
HighFree:           4124 kB
LowTotal:         873952 kB
LowFree:          144668 kB
SwapTotal:       3991892 kB
SwapFree:        3991892 kB
Dirty:                44 kB
Writeback:             0 kB
AnonPages:        624440 kB
Mapped:           114140 kB
Shmem:             85704 kB
Slab:              93440 kB
SReclaimable:      74500 kB
SUnreclaim:        18940 kB
KernelStack:        2960 kB
PageTables:         9988 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5018088 kB
Committed_AS:    1916716 kB
VmallocTotal:     122880 kB
VmallocUsed:       31268 kB
VmallocChunk:      65148 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB


---

