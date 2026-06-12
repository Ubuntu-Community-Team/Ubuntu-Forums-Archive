---
title: "My 2nd CPU core is missing"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by mbzn on 2010-06-13
Hi, since 10.04(fresh install) my CPU only shows one core in Sysinfo and MGM System monitor. How can I confirm that both CPU cores are enabled?

Thanx in advance

---

### Post by Diabolis on 2010-06-13
It might be putting together the data from both cpus. Check by yourself how many cpus is listing your OS:
```

 ls -l /sys/devices/system/cpu/

```

---

### Post by mbzn on 2010-06-13
Thanks, that was my thought as i haven't noticed a significant decrease in performance. Although this is my output, what does it mean?

```
total 0
drwxr-xr-x 4 root root    0 2010-06-13 15:07 cpu0
drwxr-xr-x 2 root root    0 2010-06-13 15:08 cpufreq
drwxr-xr-x 2 root root    0 2010-06-13 15:08 cpuidle
-r--r--r-- 1 root root 4096 2010-06-13 17:30 kernel_max
-r--r--r-- 1 root root 4096 2010-06-13 17:30 offline
-r--r--r-- 1 root root 4096 2010-06-13 17:30 online
drwxr-xr-x 2 root root    0 2010-06-13 17:30 perf_events
-r--r--r-- 1 root root 4096 2010-06-13 17:30 possible
-r--r--r-- 1 root root 4096 2010-06-13 17:30 present
-rw-r--r-- 1 root root 4096 2010-06-13 17:30 sched_mc_power_savings
```

---

### Post by Diabolis on 2010-06-13
Is listing one cpu :-(
> 
drwxr-xr-x 4 root root    0 2010-06-13 15:07 cpu0


Some fixed it by enabling ACPI, see this thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1430419](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1430419)

---

### Post by bumanie on 2010-06-13
> cat /proc/cpuinfo will give all the stats about your cpu

---

### Post by mbzn on 2010-06-13
cat /proc/cpuinfo gave me this:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2399.965
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4799.93
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

Which is funny accept if my cpu was stolen and replaced by someone
It used to be a E6600

---

### Post by mbzn on 2010-06-13
@Diabolis, Just checked the bios and have no option for ACPI.

Now what???

EDIT: My mobo is a gigabyte S-series GA-G31MX-S2

---

### Post by bumanie on 2010-06-13
Try this in terminal, it should list how may cores there are runnning and at what speed they are running at present, which may be below their actual potential if you are not running heavy apps > hwinfo --cpu --short
You may have to install hardware info first > sudo apt-get install hwinfo

---

### Post by mbzn on 2010-06-13
only one core again

```
hwinfo --cpu --short
cpu:                                                            
                       Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz, 2475 MHz

```

---

### Post by bumanie on 2010-06-13
Well that certainly indicates that there is only one core running and that it is running at maximum speed - I have no idea how to get ubuntu to see the other core - other than I once saw another poster with this issue who was using 32bit ubuntu and when they changed to 64bit, both cores were seen. If you are running 32bit, you could try the 64bit and see what happens. You should put a bug report into launchpad and add the outputs of the commands you have used.

---

### Post by mbzn on 2010-06-13
Already on 64bit. Will do the bug report.
Thanks for the help...

---

### Post by cascade9 on 2010-06-13
It could always be a faulty/dead core....but that is going to be a real pain to diagnose unless you have spare motherbaords/CPUs hanging around :|

---

### Post by mbzn on 2010-06-13
Both cores confirmed working in windows and earlier Ubuntu releases(live cd's).
ACPI reported no problem during POST, on boot i get "ACPI [OK]"
What other info can i put in the bug report, or any more suggestions?

---

### Post by archenroot on 2011-03-23
I also had troubles with Ubuntu Server 10.04, kernel in use is 2.6.32-31-server, there was only one core detected on my Q9550 CPU, and it was fixed by setting up ACPI support in BIOS in the correct way. 

After reading this post, I think here described issue is not related to bad set up of ACPI...but don't know exactly.

Ladislav

---

### Post by Dutch70 on 2011-03-23
Are you running Ubuntu in a virtual machine?

---

### Post by coolbrook on 2011-03-23
[COLOR=Silver]Do you have the 'generic' kernel installed?

Terminal:[/COLOR] [COLOR=Silver]

uname -r

[COLOR=Black]Edit: Disregarding old thread[/COLOR]
[/COLOR]

---

