---
title: "Doesn't Dual Core work on 64 Intrepid?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by jou770d on 2009-03-02
I've been using Ubuntu for a long time but I've only switched to 64 recently.
I've noticed that the system monitor only lists my CPU as a whole instead of two cores.

This is the output I get when running ```

sudo cat /proc/cpuinfo
```

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping	: 6
cpu MHz		: 2534.000
cache size	: 6144 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5053.95
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Is this normal because I'm using 64 or is there anything I can do to make the dual cores work?

By the way the device I'm working on is an Asus laptop (M51VA-AS024C).

---

### Post by 73ckn797 on 2009-03-02
There was not another section after that one that started with"processor      :1"?

---

### Post by kelvin spratt on 2009-03-02
it says no of core 1 are you sure its a duel core processor and not 64bt single core

---

### Post by jou770d on 2009-03-02
Thanks for the replies!

> **73ckn797 said:**
> There was not another section after that one that started with"processor      :1"?
Nope, that's the whole thing. But this is the output from an Intrepid 32 live cd that I'm posting from right now.

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5053.95
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 5053.91
clflush size	: 64
power management:

```

> **kelvin spratt said:**
> it says no of core 1 are you sure its a duel core processor and not 64bt single core

Unless I've misunderstood something (which is possible) it is a dual core processor: [http://ark.intel.com/cpu.aspx?groupID=35562](http://ark.intel.com/cpu.aspx?groupID=35562)
Please correct me if I'm wrong.

Thanks in advance.

---

### Post by kelvin spratt on 2009-03-02
Yes the live cd confirms that OK no of cores 2, But how its only showing 1 core is a bit baffling?

---

### Post by jou770d on 2009-03-02
To make things more fun (read annoying) I've burned and tested a 64 live cd and it also reported two cores.
That made me think that it might be a kernel update that screwed this but booting with the same kernel used on the cd didn't change anything.

---

### Post by fooman on 2009-03-02
what kernel are you running?

please post the output of:

```
uname -a
```

---

### Post by jou770d on 2009-03-02
> **fooman said:**
> what kernel are you running?

please post the output of:

```
uname -a
```

Using the latest generic:
```
amarus@Zeus:~$ uname -a
Linux Zeus 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

The one I tried switching to was 2.26.27-7.

---

### Post by LowSky on 2009-03-02
do me a favor go to System> Admin > System Monitor

Under the System Tab it will list the Release Kernel and Hardware
could you show us the screenshot?

heres mine

---

### Post by jou770d on 2009-03-02
Here you go:

---

### Post by LowSky on 2009-03-02
Does this happen in Windows?

Are you using 'acpi=off' boot parameter  to boot your machine?

---

### Post by jou770d on 2009-03-02
> **LowSky said:**
> Does this happen in Windows?

Are you using 'acpi=off' boot parameter  to boot your machine?

No for both questions.
However my windows installation (Vista Ultimate) is 32bits.
And should I try using that parameter or are you just making sure that I'm not using it?

Thanks for your help.

---

### Post by stalkier on 2009-03-02
> **LowSky said:**
> do me a favor go to System> Admin > System Monitor

Under the System Tab it will list the Release Kernel and Hardware
could you show us the screenshot?

heres mine

HEY!! My laptop is also called John-Laptop..... :D

---

### Post by jou770d on 2009-03-03
Solved!
When you told me to check apic=off I've searched for the exact in my grub's menus.lst. Now that I'm not as sleepy as I was yesterday, I've took another look and found "noapic", "nolapic" and "irqpoll".
Took them off, booted and I have my two cores working now. Although I'm not sure entierly what I did there.
(I figured that as long as I know how to restore my old grub list what's the worth that could happen?)

But is there any kind of begineers guide to kernel parameters??
I've found lists of them but I can't find something that explains the point of using each.

---

