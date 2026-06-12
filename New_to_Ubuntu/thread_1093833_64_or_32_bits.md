---
title: "64 or 32 bits"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-03-12
how do i chek whether i have 32 or 64 bit computer "??

how to find this ???

---

### Post by pbpersson on 2009-03-12
When you first boot up your system you can look in the BIOS and see what sort of processor you have.  For instance, the machine I am typing on has an AMD Athlon 64 X2 Dual Core 4200+

---

### Post by Kareeser on 2009-03-12
It depends on your processor.

Run this command:
```
lshw -C cpu
```

See "Width".

---

### Post by kimikrishna on 2009-03-12
[B][I][U]width: 64 bits
[/U][/I][/B]

so..  i use 64 bit computer ....dont i ?

---

### Post by Kareeser on 2009-03-12
That value denotes that your processor is capable of supporting 64-bits. However, it is possible to install a 32-bit operating system onto it, which, while it will run properly, will not be utilizing your processor cores to its full potential.

To check to see whether ubuntu is running 32-bits or 64, run this command:
```
sudo uname -m
```

64-bit ubuntu will have "_x86" appended to the end.

---

### Post by martrn on 2009-03-12
> **kimikrishna said:**
> [B][I][U]width: 64 bits
[/U][/I][/B]so..  i use 64 bit computer ....dont i ?

Yes ...

... a cpu with of 64bit is a 64 bit cpu (or 64bit computer).  Install a 64bit operating system if you can.

---

### Post by deepclutch on 2009-03-12
in a livecd:
```
 cat /proc/cpuinfo 
```
ofcourse ,Ubuntu 8.10 64-bit is working fine for me.

---

### Post by bodhi.zazen on 2009-03-12
An interesting tip :

```
grep ' lm ' /proc/cpuinfo --color=auto
```

The lm option in "flags" = a 64 bit cpu. I have found this the most reliable way of identifying 64 bit cpu.

uname -m / uname -p identifies the kernel you are currently running, but not what the cpu is capable of (if you are running 32 bit on a 64 bit processor, uname will return 32 bit processor ).

---

### Post by kimikrishna on 2009-03-12
> **bodhi.zazen said:**
> An interesting tip :

```
grep ' lm ' /proc/cpuinfo --color=auto
```

The lm option in "flags" = a 64 bit cpu. I have found this the most reliable way of identifying 64 bit cpu.

uname -m / uname -p identifies the kernel you are currently running, but not what the cpu is capable of (if you are running 32 bit on a 64 bit processor, uname will return 32 bit processor ).
i got this for uname : i686 (so what i am having ? )

i got this for bodhi.zzen : 
```
krishna@ubuntu:~$ grep ' lm ' /proc/cpuinfo --color=auto
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm
```

---

### Post by kimikrishna on 2009-03-12
so what now ?? 
i am having 64 bit computer ....

but what about my ubuntu ?? is it 64 ? 
thnxx

---

### Post by SunnyRabbiera on 2009-03-12
For that you can go to system> administration > system monitor
check the first tab out for your OS info.

(cool, according to lshw -C cpu I can run a 64bit OS on this puppy, I have P4 but thought it was made before the P4 became 64bit compatible)

---

### Post by ubudog on 2009-03-12
Just run uname -a in a terminal and post the results.

---

### Post by bodhi.zazen on 2009-03-12
> **kimikrishna said:**
> i got this for uname : i686 (so what i am having ? )

i got this for bodhi.zzen : 
krishna@ubuntu:~$ grep ' lm ' /proc/cpuinfo --color=auto
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **[SIZE=2]lm[/SIZE]** constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **[SIZE=2]lm[/SIZE]** constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm

This is the "problem" with uname.

You have a 64 bit CPU as shown by the "lm" flag (I bolded it in your output).

uname shows us you are running 32 bit Ubuntu (output i686).

If you like, download the 64 bit desktop iso and fire it up, you will see the output of uname changes.

It would help others if you will take the time to confirm this as they are still advising uname.

(Wisdom is the ability to recognise a mistake when you are repeating it again, and I made the same mistake with uname more times then I care to admit. I appreciate the comunity member who pointed it out to me although I do not recall who it was).

---

### Post by ubudog on 2009-03-12
You have 32bit.

---

### Post by bodhi.zazen on 2009-03-12
> **ubudog said:**
> You have 32bit.

he he he ...

Not true. If you wish, boot a 64 bit processor with a 32 bit version of Ubuntu and look at the output of uname -a or uname -p

Then boot it with a 64 bit versions and repeat :)

I bet you will be surprised, I *know* I was.

---

### Post by ubudog on 2009-03-12
She said "I got this for uname:i686 and that is 32 bit. Maybe I misunderstood.

---

### Post by bodhi.zazen on 2009-03-12
> **ubudog said:**
> She said "I got this for uname:i686 and that is 32 bit. Maybe I misunderstood.

Sorry if I was not clear, but uname identifies the Operating system as 32 or 64 bit, not the cpu.

Your interpretation of the output is fine, your understanding of uname is a bit off, and as I said I had this problem too.

As I said, when you get a chance, boot a 64 bit CPU with both a 64 bit and 32 bit version of Ubuntu and watch the output of uname change.

If you look up, the lm flag I bolded is in my experience the most reliable marker of a 64 bit CPU (although you can of course look at other items in the output of cat /proc/cpuinfo).

---

### Post by Simian Man on 2009-03-12
Guys uname gives info about the *OS* running, not the machine underneath.  Looking at /proc/cpuinfo will tell you what processor you have.  Then a simple google should reveal if it is a 64 bit processor or not.

Alternatively, you could just put in a 64-bit Live CD and see if it runs.  If so, congrats, you have a 64-bit system :).

---

### Post by ubudog on 2009-03-12
Ahh.  Now I understand.

---

### Post by philinux on 2009-03-12
Another **hardware** check is this.

lshw | grep cpu

Mine shows this. Note the x86-64=64 bit processor.
> lshw | grep cpu
WARNING: you should run this program as super-user.
     *-cpu                
          bus info: cpu@0
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp **x86-64** 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq


---

### Post by kimikrishna on 2009-03-14
@ ALL 

THANKS ...   i have now understood that i have 64-bit procsr with 32-bit ubuntu installed.....!! 

thanks

---

### Post by KayakJim on 2009-03-14
i686 is typically referring to a 64-bit version.

**Correction:** i686 is for 32-bit.

---

### Post by oldos2er on 2009-03-14
> **KayakJim said:**
> i686 is typically referring to a 64-bit version.

 i686 is strictly 32-bit.

---

### Post by boof1988 on 2009-03-14
> **KayakJim said:**
> i686 is typically referring to a 64-bit version.

I believe that is incorrect.

For the output of *uname*:

x86_64 indicates a 64-bit OS
i686 indicates a 32-bit OS

I'm trying to find a good source to verify this... Will post it when I find it, unless someone else confirms this before I can locate a source.

---

### Post by KayakJim on 2009-03-14
> **boof1988 said:**
> I believe that is incorrect.

For the output of *uname*:

x86_64 indicates a 64-bit OS
i686 indicates a 32-bit OS

I'm trying to find a good source to verify this... Will post it when I find it, unless someone else confirms this before I can locate a source.

That is correct. Please excuse my mistype. My kids had me distracted.

i686 is indeed 32-bit.

---

### Post by martrn on 2009-03-14
i686, is a compiler flat to compile software for the Intel Pentium Pro CPU. or Intel Pentium II cpu (or higher),

[URL="http://gcc.gnu.org/onlinedocs/gcc-3.4.4/gcc/i386-and-x86_002d64-Options.html"]
http://gcc.gnu.org/onlinedocs/gcc-3.4.4/gcc/i386-and-x86_002d64-Options.html[/URL]

---

### Post by kimikrishna on 2009-03-14
i have core2duo with 3Ghz frequency.....

but still run 32 bit ubuntu........ 

i got cd to home.... but ubuntu sent me only 32 bit.... :(

---

### Post by steve101101 on 2009-03-14
i have a quad core with 4gb of ram, however I still feel the support for 64 bit is not good enough to make up for its benefits.

---

