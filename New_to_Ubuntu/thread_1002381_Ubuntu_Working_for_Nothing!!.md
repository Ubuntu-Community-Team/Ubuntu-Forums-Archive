---
title: "Ubuntu Working for Nothing??!!??"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by fishman78 on 2008-12-04
Hey Everyone,

    Quick question about my ubuntu 8.10 64bit.  I purchased new hardware and re-imaged my hard drive on a new PC.  I didn't notice before, but it looks like 1 of my CPUs is always working at 60-70% while the other is idle.  According to the system monitor, I should only be using 15% for Xorg.  Is this normal behaviour, or is something wrong with my install?  Thanks for all the help!!

fishman78

---

### Post by handydan918 on 2008-12-04
> **fishman78 said:**
> Hey Everyone,

    Quick question about my ubuntu 8.10 64bit.  I purchased new hardware and re-imaged my hard drive on a new PC.  I didn't notice before, but it looks like 1 of my CPUs is always working at 60-70% while the other is idle.  According to the system monitor, I should only be using 15% for Xorg.  Is this normal behaviour, or is something wrong with my install?  Thanks for all the help!!

fishman78
How about posting the output of ```
cat /proc/cpuinfo
```
and > uname -r

I'm of to la-la land pretty quick, but I'll bet somebody will pick it up for you...

---

### Post by fishman78 on 2008-12-04
Howdy!  

  Here is one:

[COLOR=Blue]ubuntu@ubuntu-laptop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
stepping    : 2
cpu MHz        : 2800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 5599.86
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
stepping    : 2
cpu MHz        : 2800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 5599.86
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

[COLOR=Black]And the other:

[COLOR=Blue]ubuntu@ubuntu-laptop:~$ uname -r
2.6.27-9-generic

[COLOR=Black]Hope this helps!  Thanks for your input!![/COLOR]
[/COLOR]
[/COLOR][/COLOR]

---

### Post by fishman78 on 2008-12-05
Should I maybe try and re-install ubuntu?  This isn't an option I would really want to explore, but I feel this unexplained CPU usage is really hindering performance.  Thanks again for all your responses.

---

### Post by nhasian on 2008-12-05
system monitor takes up lots of system resources itself.  in a terminal just type

```
top
```

what processes are taking up the most CPU time?

are these processes single threaded or multithreaded?

---

### Post by fishman78 on 2008-12-05
> **nhasian said:**
> system monitor takes up lots of system resources itself.  in a terminal just type

```
top
```

what processes are taking up the most CPU time?

are these processes single threaded or multithreaded?

hmmm, that's a good point.  I will look into that when I get home tonight.  It wouldn't have anything to do with the fact that the image came from a different PC would it?  After looking at the output I posted I noticed that It's showing my CPU @ 2.8Ghz when it should be 3.1Ghz.  Maybe something is a little wonky??  Thanks again!

---

### Post by Ayuthia on 2008-12-05
> **fishman78 said:**
> hmmm, that's a good point.  I will look into that when I get home tonight.  It wouldn't have anything to do with the fact that the image came from a different PC would it?  After looking at the output I posted I noticed that It's showing my CPU @ 2.8Ghz when it should be 3.1Ghz.  Maybe something is a little wonky??  Thanks again!

Ubuntu will adjust the speed when needed so the number can fluctuate.  Mine goes anywhere between 800 to 1800.

Are you using any additional kernel boot parameters?  If you are not sure, can you post the results of:
```
cat /proc/cmdline
```

EDIT: I forgot to mention that the boot parameters are usually added in GRUB in the /boot/grub/menu.lst file.  They are commands that are used to adjust the kernel before it starts up.  They could be things like noapic, acpi=off, etc.

---

### Post by fishman78 on 2008-12-05
> **Ayuthia said:**
> Ubuntu will adjust the speed when needed so the number can fluctuate.  Mine goes anywhere between 800 to 1800.

Are you using any additional kernel boot parameters?  If you are not sure, can you post the results of:
```
cat /proc/cmdline
```

Thanks!  However, I have no idea if I am using any extra boot parameters.  I will post the output tonight when I get home.  Thanks for the suggestion.

---

### Post by fishman78 on 2008-12-05
> **nhasian said:**
> system monitor takes up lots of system resources itself.  in a terminal just type

```
top
```

what processes are taking up the most CPU time?

are these processes single threaded or multithreaded?


You were right.  Without System Monitor running I'm only usuing in and around 8-20%.  Yeesh!  That system monitor is a resource pig!!  Thank your for the TOP command.  

As for running extra kernel boot parameter, this is the out from the CAT command

ubuntu@ubuntu-laptop:~$ cat /proc/cmdline
root=UUID=7e6770c7-99f3-4089-ad87-84f495b4605b ro quiet splash 


Thanks again for all your help!!!

---

