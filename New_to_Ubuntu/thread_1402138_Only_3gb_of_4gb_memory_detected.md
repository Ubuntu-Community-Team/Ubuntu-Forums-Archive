---
title: "Only 3gb of 4gb memory detected"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by mafaldaspeaks on 2010-02-08
I just installed Ubuntu 9.1 on a laptop that has 4gb of memory. Ubuntu however only detects 3gb. Could someone please explain why this is so?

---

### Post by nwadams on 2010-02-08
you are most likely using the 32 bit version which can only "see" 3.2 gb of ram.

post the output of 
```
uname -a
```

hope this helps

---

### Post by Locke_99GS on 2010-02-08
You'll need a PAE kernel or 64 bit to see more ram.

---

### Post by mafaldaspeaks on 2010-02-08
> **nwadams said:**
> you are most likely using the 32 bit version which can only "see" 3.2 gb of ram.

post the output of 
```
uname -a
```

hope this helps

I'll try that when I get home. In the computer store where I bought the laptop they said the computer was 32-bit so I installed ubuntu's 32-bit version.

Will the 64-bit work even if my laptop's 32-bit?

---

### Post by nwadams on 2010-02-08
i assume since it has 4gb of ram that it is a new computer. Yes it will support 64 bit. Any cpu in the last 3 years should support 64 bit (atom not withstanding)

---

### Post by sisco311 on 2010-02-08
> **mafaldaspeaks said:**
> 
Will the 64-bit work even if my laptop's 32-bit?

Nope, in that case you need the PAE kernel:
[uhelp]community/EnablingPAE[/uhelp]

But, if
```
grep --color=always " lm " /proc/cpuinfo
```
returns any output,  you have a 64 bit CPU & you can install the 64bit version.

---

### Post by NightwishFan on 2010-02-08
No, you will need 64-bit capable hardware to use 64-bit Ubuntu. I am not sure if there is a PAE kernel. I believe the Server one is, however it is not geared toward desktop use.

---

### Post by EssexEagle on 2010-02-08
> **NightwishFan said:**
> No, you will need 64-bit capable hardware to use 64-bit Ubuntu. I am not sure if there is a PAE kernel. I believe the Server one is, however it is not geared toward desktop use.

I'm running Kubuntu 9.10 and have a PAE kernel... although I never intentionally installed it!  Either it's the kernel that comes on the Kubuntu Karmic Live CD, or I got it through an update soon after installing Karmic :confused:

---

### Post by mafaldaspeaks on 2010-02-08
> **sisco311 said:**
> Nope, in that case you need the PAE kernel:
[uhelp]community/EnablingPAE[/uhelp]

But, if
```
grep --color=always " lm " /proc/cpuinfo
```
returns any output,  you have a 64 bit CPU & you can install the 64bit version.

I'll try the code when I get home. But do I understand right, even if my laptop's 32-bit, I can just enable PAE and then install the 64-bit version of ubuntu?

And this will be more efficient for the laptop?

---

### Post by Philip550c on 2010-02-08
Might be because of the 32 bit - 64 bit issue but i bet its just shared memory with the video card combined with the fact that a gigabyte is 1024mb not 1000mb.

---

### Post by sisco311 on 2010-02-08
> **mafaldaspeaks said:**
> I'll try the code when I get home. But do I understand right, even if my laptop's 32-bit, I can just enable PAE and then install the 64-bit version of ubuntu?

And this will be more efficient for the laptop?

No, if you have a 32bit CPU, your only option is to install the PAE kernel which will recognize all your RAM.

If you have a 64bit CPU, you have two options:
- install the PAE kernel & keep the 32bit environment 
or 
- install the 64bit version of Ubuntu.

---

### Post by cascade9 on 2010-02-08
> **Philip550c said:**
> Might be because of the 32 bit - 64 bit issue but i bet its just shared memory with the video card combined with the fact that a gigabyte is 1024mb not 1000mb.

It could very well be shared memory. But as for the 1024/1000 issue, only hard drive manufacturers play silly buggers like that, RAM manufacturers know that 1024K=1MB, 1024MB=1GB, 1024GB=1TB, etc.

---

### Post by EssexEagle on 2010-02-08
> **Philip550c said:**
> Might be because of the 32 bit - 64 bit issue but i bet its just shared memory with the video card combined with the fact that a gigabyte is 1024mb not 1000mb.

No, it's definitely the 32- vs. 64-bit issue (Google/Wikipedia it :))

---

### Post by Michellea101 on 2010-02-08
> **cascade9 said:**
> It could very well be shared memory. But as for the 1024/1000 issue, only hard drive manufacturers play silly buggers like that, RAM manufacturers know that 1024K=1MB, 1024MB=1GB, 1024GB=1TB, etc.

I just meant that some programs will show the ram higher and some lower because of the way that program is calculating the amount of ram.

EDIT: Sorry I'm on my girlfriends laptop, didnt notice I was signed in under her name. This is Philip550c.

---

### Post by Michellea101 on 2010-02-08
> **EssexEagle said:**
> No, it's definitely the 32- vs. 64-bit issue (Google/Wikipedia it :))

I know the difference, thats why I run 64 bit;) But many laptops share system ram with the videocard. My laptop has 2gb but 400mb or so is used by my ati radeon card. 1gb of shared memory is a lot if this were the case but not impossible. Would be good to know the hardware of the OP to better narrow down the possibilities.

EDIT: Sorry I'm on my girlfriends laptop, didn't notice I was signed in under her name. This is Philip550c.

---

### Post by 73ckn797 on 2010-02-08
The PAE kernel can be installed via Synaptic Package Manager. I have had it installed automatically during a fresh install and another I manually installed it. I use it on a desktop computer.

---

### Post by mafaldaspeaks on 2010-02-09
> **sisco311 said:**
> No, if you have a 32bit CPU, your only option is to install the PAE kernel which will recognize all your RAM.

If you have a 64bit CPU, you have two options:
- install the PAE kernel & keep the 32bit environment 
or 
- install the 64bit version of Ubuntu.
Ok, this helps clarify what I can do after I've verified my CPU. Thanks!

---

### Post by jward3010 on 2010-02-09
> **mafaldaspeaks said:**
> In the computer store where I bought the laptop they said the computer was 32-bit so I installed ubuntu's 32-bit version.
That is doubtful, to me it would be unusual if a manufacturer installed 4GB of RAM on a 32-bit setup. It's possible but highly unlikely.

---

### Post by fromthehill on 2010-02-09
most likely your cpu will support 64-bit
every CPU made in the last 3 years can run 64-bit
older laptops usually don't have 4GB. And I've never heard of an ATOM with 4GB memory

---

### Post by warfacegod on 2010-02-09
> **cascade9 said:**
> It could very well be shared memory. But as for the 1024/1000 issue, only hard drive manufacturers play silly buggers like that, RAM manufacturers know that 1024K=1MB, 1024MB=1GB, 1024GB=1TB, etc.

I think recordable discs are the same way but I'm not sure.

---

### Post by warfacegod on 2010-02-09
> **Philip550c said:**
> Might be because of the 32 bit - 64 bit issue but i bet its just shared memory with the video card combined with the fact that a gigabyte is 1024mb not 1000mb.

1 GB of shared RAM is unlikely but not impossible. 1024/1000 from 4 GB = 96 MB difference. That's not enough to account for it.

---

### Post by mafaldaspeaks on 2010-02-09
> **nwadams said:**
> you are most likely using the 32 bit version which can only "see" 3.2 gb of ram.

post the output of 
```
uname -a
```

hope this helps

Here it is:

Linux mafalda 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux

What does it mean?

---

### Post by mafaldaspeaks on 2010-02-09
> **sisco311 said:**
> 

But, if
```
grep --color=always " lm " /proc/cpuinfo
```
returns any output,  you have a 64 bit CPU & you can install the 64bit version.
This is what I got:

flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm

Just as I asked about the other code, please explain what this means. Thanks!

---

### Post by sisco311 on 2010-02-09
> **mafaldaspeaks said:**
> 
Just as I asked about the other code, please explain what this means. Thanks!

```
**grep** [COLOR="Red"]--color=always[/COLOR] [COLOR="Blue"]" lm "[/COLOR] /proc/cpuinfo
```

If the [COLOR="Blue"]lm[/COLOR] flag is present, print the /proc/cpuinfo file's flag line.

```
**grep** [COLOR="Red"][OPTIONS][/COLOR] [COLOR="Blue"]PATTERN[/COLOR] [FILE...]
```

**grep** searches the named input FILEs for lines containing  a  match to the given [COLOR="Blue"]PATTERN[/COLOR].  By default, grep prints the matching lines.

[COLOR="Red"]--color=always[/COLOR] = display the matched lines in color.

[color="Blue"]" lm "[/color] = the search pattern, the lm flag means Long Mode = 64bit CPU.  

/prc/cpuinfo = file name, the file contains information about the CPU, such as its vendor (and CPU family, model and model names) and its speed , cache size, number of siblings, cores, and CPU flags.


```
uname -a
Linux mafalda 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
```

uname = print certain system information
-a = print all information

Linux = the kernel name
mafalda = hostname
2.6.31-9-rt = kernel release 
#152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 = kernel version
i686 = machine hardware name 
GNU/Linux = operating system

For details see:
```
man grep
man uname
```
[http://en.wikipedia.org/wiki/Procfs#Linux](http://en.wikipedia.org/wiki/Procfs#Linux)

So, in short, you are running a 32bit Ubuntu on a 64bit system.

You can either install the PAE kernel in your current 32bit Ubuntu or install a new 64bit Ubuntu.

---

### Post by x C0MMAND0 x on 2010-02-09
First I would check in computer bios to see if your motherboard even recognizes 4gb of memory.  If it does, then you know that you can install a 64bit os, otherwise your computer would not have been able to read the 4gb of memory in the first place.

---

### Post by mafaldaspeaks on 2010-02-09
> **sisco311 said:**
> ```
**grep** [COLOR="Red"]--color=always[/COLOR] [COLOR="Blue"]" lm "[/COLOR] /proc/cpuinfo
```

If the [COLOR="Blue"]lm[/COLOR] flag is present, print the /proc/cpuinfo file's flag line.

```
**grep** [COLOR="Red"][OPTIONS][/COLOR] [COLOR="Blue"]PATTERN[/COLOR] [FILE...]
```

**grep** searches the named input FILEs for lines containing  a  match to the given [COLOR="Blue"]PATTERN[/COLOR].  By default, grep prints the matching lines.

[COLOR="Red"]--color=always[/COLOR] = display the matched lines in color.

[color="Blue"]" lm "[/color] = the search pattern, the lm flag means Long Mode = 64bit CPU.  

/prc/cpuinfo = file name, the file contains information about the CPU, such as its vendor (and CPU family, model and model names) and its speed , cache size, number of siblings, cores, and CPU flags.


```
uname -a
Linux mafalda 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
```

uname = print certain system information
-a = print all information

Linux = the kernel name
mafalda = hostname
2.6.31-9-rt = kernel release 
#152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 = kernel version
i686 = machine hardware name 
GNU/Linux = operating system

For details see:
```
man grep
man uname
```
[http://en.wikipedia.org/wiki/Procfs#Linux](http://en.wikipedia.org/wiki/Procfs#Linux)

So, in short, you are running a 32bit Ubuntu on a 64bit system.

You can either install the PAE kernel in your current 32bit Ubuntu or install a new 64bit Ubuntu.

Wow, this really helps a lot. I think I'll install the 64bit version. Thank you sisco311 and all for your replies!

---

### Post by warfacegod on 2010-02-09
If your computer is sluggish in 64 Bit, wait it out a few days. It sounds counterintuitive but I've seen it happen. 64 Bit sometimes needs a "breaking in" period.

---

### Post by pallabbasu1234 on 2010-04-17
Is it a good idea to use PAE kernel?, how to do that?

---

### Post by NightwishFan on 2010-04-17
Use a PAE kernel only if you strictly need 32-bit. Considering that 64-bit can run 32-bit software....

---

