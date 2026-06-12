---
title: "How to easily identify whether I am 32bit or 64bit?"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by cozski on 2010-05-29
Hello

Is there a simple terminal command I can use to do this or do I have to use some other method? Thanks.

---

### Post by howefield on 2010-05-29
Are you talking about whether or not your Ubuntu install is 32 or 64 bit, or whether your machine is capable ?

Use the command

```
uname -a
```

to find out whether your Ubuntu install is 32 or 64 bit.

x86_64 in the output would indicate 64 bit.

---

### Post by mikewhatever on 2010-05-29
The OS or the cpu?

---

### Post by cascade9 on 2010-05-29
If you want to know the capablilites of the system, not what is installed, then this is the command- 

lshw

Then look at the CPU flags/capablilities- 

```
*-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv

``` 

If you get 'lm' or 'x86-64' in capabilities field, your system will run AMD64 (x86-64).

---

### Post by cozski on 2010-05-29
Sorry... I guess both. It's mainly for trying to install the correct Flash player... thanks.

---

### Post by howefield on 2010-05-29
> **cozski said:**
> It's mainly for trying to install the correct Flash player

Then, you want to know whether your operating system is 32 or 64 bit. (you couldn't install 64 bit flash into 32 bit operating system, irrespective of what the machine is capable of)

---

### Post by cozski on 2010-05-29
It produced this
> 
*-cpu
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm pse cpufreq

...and the uname -a command produced this

> Linux cozski-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

---

### Post by cascade9 on 2010-05-29
32bit OS, and a 32bit only system ;)

---

### Post by cozski on 2010-05-29
Okay, thanks for that, appreciated. :)

---

