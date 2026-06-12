---
title: "Upgrade to 64bit?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by emoguitarist06 on 2010-07-19
After reading some forums I am planning and thinking of upgrading my Karmic 32bit to Karmic 64bit.


[COLOR="Red"]**I have an Asus Eee Pc 1201N which has a 1.6GHz Intel Atom Dual Core 330 Processor & 4GB of Ram**[/COLOR]

I currently have my **/home **on a **separate partition**
so if I was to install 64bit what files would I lose any files? As I would only be formating the root partition? Or do I have to format my /home partition?

---

### Post by howefield on 2010-07-19
Should work fine by formatting / and not /home.

---

### Post by emoguitarist06 on 2010-07-19
> **howefield said:**
> Should work fine by formatting / and not /home.

Great! However what kind of like configs/settings would I be losing? Since I'll be formatting /etc & /bin & /lib... etc..
I personally don't know what exactly goes in those folders

I would however of course need to reinstall all my programs correct?

---

### Post by baddnady23 on 2010-07-19
If you have your /home on a separate partition, then all your personal documents, music, photos and such should be saved.  Ubuntu also saves all of your program configuration settings to your /home folder.  These folders are just hidden.  Go into your /home folder and hit ctrl+h and it will show them. 

When you install the new 64 bit version, given that you don't overwrite your /home partition, all those folders that were in it before will remain there.  However, you will need to reinstall the programs/packages that you used in your Ubuntu distro as these will not transfer over when you reinstall.  I usually just make a text document and write down everything that I want to reinstall and just save it to /Documents.

As always, BACKUP your /home before making changes.  Things do go wrong every now and then.

---

### Post by lukeiamyourfather on 2010-07-19
> **emoguitarist06 said:**
> Great! However what kind of like configs/settings would I be losing? Since I'll be formatting /etc & /bin & /lib... etc..
I personally don't know what exactly goes in those folders

I would however of course need to reinstall all my programs correct?

Anything in your home directory like music files would be untouched. Some application preferences like Firefox are stored in the home directory, but not all. Everything else will be lost including installed packages and software. Cheers!

EDIT: baddnady23 beat me to it.

---

### Post by 3Miro on 2010-07-19
> **emoguitarist06 said:**
> 
[COLOR="Red"]**I have an Asus Eee Pc 1201N which has a 1.6GHz Intel Atom Dual Core 330 Processor & 4GB of Ram**[/COLOR]


Are you sure Atoms support 64-bit. Get a live CD or live Flash to test it first. Intel web-page says 64-bit instruction set, but I am not sure if this is equivalent to EMT64 (which is required for 64-bit OS on Intel CPU).

The only thing that you will need to format is /, if /home is on separate partition, it should be safe. However, there is always a chance that something can go wrong, so it will be best if you backup all of your data first.

---

### Post by emoguitarist06 on 2010-07-19
> **3Miro said:**
> Are you sure Atoms support 64-bit. Get a live CD or live Flash to test it first. Intel web-page says 64-bit instruction set, but I am not sure if this is equivalent to EMT64 (which is required for 64-bit OS on Intel CPU).

The only thing that you will need to format is /, if /home is on separate partition, it should be safe. However, there is always a chance that something can go wrong, so it will be best if you backup all of your data first.

Yeah I'm not quite sure but I'll definately test via live cd tonight. I'm at work right now.

Thanks for all the input everyone! I'll make a final post on how it all went ;)

---

### Post by baddnady23 on 2010-07-19
Just make sure when you start telling it where to install / and /home, that you tell it to make /home the partition that your current /home is on.

---

### Post by emoguitarist06 on 2010-07-21
Output of "cat /proc/cpuinfo"

Does this mean I can run 64bit?

```
phillip@EeePC-1201N:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.088
cache size	: 512 KB
physical id	: 0
siblings	: 4
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.17
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.088
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.08
clflush size	: 64
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.088
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.01
clflush size	: 64
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.088
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.09
clflush size	: 64
power management:

phillip@EeePC-1201N:~$ 


```

---

### Post by bodhi.zazen on 2010-07-21
Yes that is a 64 bit processor.

---

### Post by skompier on 2010-07-21
I was running 64bit but went back to 32bit because of the Flash issues with 64bit. I'm running the 32bit PAE kernel so I can use my 4GB of memory

---

### Post by cjv8888 on 2010-07-22
or use the alpha issue of the 64 bit flash which I installed and seems to work perfectly well in my system.

---

### Post by Sef on 2010-07-22
> After reading some forums I am planning and thinking of upgrading my Karmic 32bit to Karmic 64bit.


Just to be clear, the only way to upgrade a 32-bit system to a 64-bit system is to install the 64-bit over the 32-bit system, thus deleting the 32-bit os, unless one installs the 64-bit os on different partition.

---

