---
title: "Replacing the processor"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Castor68 on 2009-04-01
Hi all. I have an my old  Compaq S5100NX. I bought a Pentium 4 socket 478, 2.4 GHz to replace the default processor (a 2.6 GHZ Celeron). My question is: after I replace the processor, will it happen problems when the computer starts or not?. If yes, what do I have to do?.

---

### Post by Volt9000 on 2009-04-01
Assuming your motherboard supports this CPU there should be no problems.
BIOS may complain initially, depending on what settings you had before, but otherwise you should have no problems.

Unless of course you seat the CPU improperly, in which case your computer will successfully pass the Smoke Test. ;)

---

### Post by Cypher on 2009-04-01
Going from the Celeron to the P4 shouldn't cause any problems. Since both the processors are single core, you need not even bother changing the Kernel into SMP mode or anything.

On your current machine, do a "cat /proc/cpuinfo" and store that information. Then swap out the processor and repeat the command and confirm that the new processor and the new speed was properly recognized..

---

### Post by egalvan on 2009-04-01
Since Socket 478 (more correctly Socket mPGA478B) accepted
many different iterations of P-IV,
 it's impossible to tell if the upgrade will work...

The only way to know for sure is to try it...

differences:

Architecture:

Willamette
Northwood
Prescott

FSB speed:
400
533
800


I have a Dell (170N) that came with a Celeron 2.2GHz / 128k cache / 400FSB
I tried a P-IV 2.8GHz / 1M cache / 800FSB
it worked. Very much improved.

I have a Dell laptop (1100) that came with a Celeron 2.6GHz / 128k cache / 400FSB
Tried the following P-IV:
2.0GHz / 512K cache / 400FSB   works well, good improvement.
2.6GHz / 512k cache / 533FSB   did not turn on.
2.8 / 1M cache / 800FSB   turned on, but just beeped.

So as I said, it depends on the motherboard chipset, and the BIOS.

---

### Post by Castor68 on 2009-04-10
I did cat /proc/cpuinfo. And I got this:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping	: 9
[COLOR="Red"]cpu MHz		: 1793.342[/COLOR]
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 3586.68
clflush size	: 64
power management:

Those 1.8 GHz are not the real speed....

---

