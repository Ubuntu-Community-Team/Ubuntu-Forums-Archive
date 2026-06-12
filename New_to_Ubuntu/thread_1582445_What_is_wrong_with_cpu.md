---
title: "What is wrong with cpu?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by lanetherif on 2010-09-26
Hi, 

I've just installed Enna. What I've seen was this: 
[[IMG]http://img828.imageshack.us/img828/2046/88558390.th.jpg[/IMG]]("http://img828.imageshack.us/i/88558390.jpg/")

It says one of cpu's working at 2800mhz. Also, there is conky which says one cpu is at 100 %.

Anybody have an idea about where I should start?

---

### Post by andrewthomas on 2010-09-26
Post the output of

```
sudo lshw -C cpu
```

---

### Post by JohnHeikkila on 2010-09-26
189% usage? That...doesn't sound right..

---

### Post by andrewthomas on 2010-09-26
also you could post the output of 

```
cpufreq-info
```

---

### Post by lanetherif on 2010-09-26
This is for lshw -C cpu 
```
*-cpu                   
       description: CPU
       product: AMD Phenom(tm) II X4 925 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Phenom(tm) II X4 925 Processor
       serial: To Be Filled By O.E.M.
       slot: CPU 1
       size: 800MHz
       capacity: 2800MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq

```

and this is for cpufrequtils:

```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.10 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:3.81%, 2.10 GHz:0.07%, 1.60 GHz:0.15%, 800 MHz:95.97%  (2049)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.10 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:4.63%, 2.10 GHz:0.07%, 1.60 GHz:0.30%, 800 MHz:94.99%  (2033)
analyzing CPU 2:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 2
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.10 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:4.65%, 2.10 GHz:0.10%, 1.60 GHz:0.29%, 800 MHz:94.96%  (2049)
analyzing CPU 3:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.10 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:4.88%, 2.10 GHz:0.06%, 1.60 GHz:0.35%, 800 MHz:94.71%  (1609)

```

By the way I've restarted the system...

---

