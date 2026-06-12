---
title: "64 bit Ubuntu on 32 bit computer."
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Ariya243 on 2011-02-01
Yesterday, by mistake I placed the 64bit Ubuntu on a 32 bit laptop. It got booted and I even installed it. I didn't realize that I am using a 64 bit Ubuntu live disk. I was always told that such could not be. I am writing from that 32 bit laptop with 64 bit Ubuntu. It doesn't fail, juts works. It is 10.04:p

How did that happen?

The laptop is Lenovo Thinkpad T400

---

### Post by coffeecat on 2011-02-01
> **Ariya243 said:**
> How did that happen?

Either the CPU is a 64-bit one and you didn't know it, or you used a 32-bit Ubuntu disc. :p Open a terminal and post the output of these two commands: 

```
lscpu
uname -a
```**EDIT**:  Aha! You slipped this in while I was posting.  :)

> **Ariya243 said:**
> The laptop is Lenovo Thinkpad T400

---

### Post by wojox on 2011-02-01
Run this in the terminal and post back:

```
grep flags /proc/cpuinfo
```

---

### Post by coffeecat on 2011-02-01
> **Ariya243 said:**
> The laptop is Lenovo Thinkpad T400

@Ariya243, a quick google reveals that the Thinkpad T400 has a Core 2 Duo CPU which is a 64-bit one.

---

### Post by sydbat on 2011-02-01
> **coffeecat said:**
> **EDIT**:  Aha! You slipped this in while I was posting.  :)

> **Ariya243 said:**
> The laptop is Lenovo Thinkpad T400[http://www.lapspecs.com/wiki/lenovo+thinkpad+t400](http://www.lapspecs.com/wiki/lenovo+thinkpad+t400)

The Windows version that came with was likely 32bit, which led you to believe it was a 32bit machine. The laptop processor (as referenced in the link) is 64bit.

---

### Post by Ariya243 on 2011-02-01
It came with Windows and it said it is 32 bit. This the out put;

 lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2401.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K
----------------
This is the 2nd output;
grep flags /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority

---

### Post by Ariya243 on 2011-02-01
uname -a
Linux Thinkpad 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

---

### Post by uRock on 2011-02-01
Your [Lenovo]("http://www.cdw.com/shop/products/default.aspx?edc=1647561") has a [64bit CPU]("http://ark.intel.com/Product.aspx?id=35568").

Cheers,
uRock

---

### Post by coffeecat on 2011-02-01
> **uRock said:**
> Your [Lenovo]("http://www.cdw.com/shop/products/default.aspx?edc=1647561") has a [64bit CPU]("http://ark.intel.com/Product.aspx?id=35568").

+1

And this proves it:

> **Ariya243 said:**
> 
 lscpu
Architecture:          [COLOR=Red]x86_64[/COLOR]
CPU op-mode(s):        32-bit, [COLOR=Red]64-bit[/COLOR]
CPU(s):                2

Your CPU is also 2-core.

And you've installed 64-bit Ubuntu:

> **Ariya243 said:**
> uname -a
Linux Thinkpad 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 [COLOR=Red]x86_64[/COLOR] GNU/Linux

So there you have it. 64-bit Ubuntu running on a 64-bit machine.

Happy Ubuntu-ing!

---

### Post by Ariya243 on 2011-02-01
Thanks guys! I have a lot of 64bit software. Now I can try all of them. Regards!

---

