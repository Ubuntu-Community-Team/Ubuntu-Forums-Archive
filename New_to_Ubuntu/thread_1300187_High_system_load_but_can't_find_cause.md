---
title: "High system load but can't find cause"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by AncientPC on 2009-10-24
I'm running Ubuntu server on a laptop.  Load reported is around 14+ with no noticeable side effects.  There is marginal CPU usage (~10%us, 4%wa), and marginal IO usage (~50K/s down and up).

I really can't understand what's causing load to be reported so high . . .

---

### Post by scorp123 on 2009-10-24
What does "top" say?
```
/usr/bin/top -b -n1
```

---

### Post by AncientPC on 2009-10-24
```
top - 21:05:00 up 87 days,  7:03,  5 users,  load average: 13.70, 13.62, 13.51
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  3.5%sy,  0.1%ni, 82.3%id,  4.7%wa,  0.1%hi,  0.3%si,  0.0%st
Mem:   1543984k total,  1295392k used,   248592k free,     3016k buffers
Swap:  1951888k total,   122292k used,  1829596k free,  1104076k cached

  PID USER      PR  NI  VIRT  RES SWAP S %CPU %MEM    TIME+  COMMAND                                 
 4051 ting      18  -2  9908 3500 6408 S  3.9  0.2 581:57.94 iotop                                   
28937 ting      18  -2 28164  20m 6904 S  3.9  1.4   3352:37 screen.real                             
31708 ting      18  -2  2444 1120 1324 R  1.9  0.1   0:00.02 top          
    1 root      20   0  1764  124 1640 S  0.0  0.0   5536:51 init                                    
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.13 kthreadd                                
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                             
    4 root      15  -5     0    0    0 S  0.0  0.0  72:54.38 ksoftirqd/0                             
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                              
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.02 events/0                                
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                 
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                 
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                           
   10 root      15  -5     0    0    0 S  0.0  0.0   0:02.12 kblockd/0                               
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.39 kacpid                                  
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.31 kacpi_notify                            
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue               

```

Truncated for brevity's sake.

---

### Post by scorp123 on 2009-10-25
> **AncientPC said:**
>  **[COLOR="Red"]load average: 13.70, 13.62, 13.51[/COLOR]**
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  3.5%sy,  0.1%ni, 82.3%id,  4.7%wa,  0.1%hi,  0.3%si,  0.0%st
Mem:   1543984k total,  1295392k used,   248592k free,     3016k buffers
Swap:  1951888k total,   122292k used,  1829596k free,  1104076k cached LOL. Yeap, that's totally weird. Usually you'd need a really powerful system to "survive" such a report from top :D

The only thing I can imagine is that for some odd reason the Ubuntu Server kernel and the CPU in that laptop don't get along so well and something is being badly misinterpreted.

What CPU is in that laptop? Can you give us this output please:
```
cat /proc/cpuinfo
```

---

### Post by AncientPC on 2009-10-25
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips        : 1595.99
clflush size    : 64
power management:

```

---

### Post by scorp123 on 2009-10-25
Hmmm ... maybe this article could help? They give various suggestions how one might troubleshoot such problems. Maybe you could try that?

[http://www.informit.com/articles/article.aspx?p=1381889&seqNum=2](http://www.informit.com/articles/article.aspx?p=1381889&seqNum=2)

---

### Post by AncientPC on 2009-10-25
Thanks for the article, but that's what has me confused is I have a low user/system CPU usage, as well as no IO usage and yet my load level is extremely high.

From the article I've double-checked that I have enough free RAM, disk space, and inodes and everything looks fine.

---

### Post by AncientPC on 2009-11-02
Load is climbing to ~22 with no difference . . .

---

