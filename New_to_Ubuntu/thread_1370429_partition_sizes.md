---
title: "partition sizes"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by albert s on 2010-01-02
hi, I am using ubuntu 9.10 and am going to put it on a "new" PC I have been given.
How much space should I give each partition?
80G HDD,
50M  = mount
1G  = swap
74G = home
and 5G for /
is 5G enough or can someone tell me better sizes? Ive never done a manual partition before, just used the guided thingy.
Thanks.

---

### Post by Cheesemill on 2010-01-02
I'd probably go for:
15GB for /
1GB for swap
Rest for /home

I don't know what you mean by 'mount'.
You may need more or less for swap depending on how much RAM you have.

---

### Post by mechro on 2010-01-02
There is no "better". It's personal preference, your goal e.g. home desktop or server etc., forward planning.

If it was my 80GB drive for a home desktop system I'd do...

1GB Swap (or 1 to 2 times RAM size)

39.5GB /  for Ubuntu A

39.5GB /  for Ubuntu B

The reason for A and B is forward planning for Upgrades or even trying different Linux distros. I wouldn't bother with a separate /home partition.

Just my opinion... it ain't necessarily "better".

---

### Post by tom.swartz07 on 2010-01-02
> **Cheesemill said:**
> I'd probably go for:
15GB for /
1GB for swap
Rest for /home

I don't know what you mean by 'mount'.
You may need more or less for swap depending on how much RAM you have.

+1 what Cheesemill said. You generally shouldn't have to specify where you want a mount partition, unless you're putting it on another drive. 

The amount of size you need for / is generally dictated by how many programs you're going to install + ~4 more gigs for any unforseen updates. Be generous. You could then just partition the rest of the drive as your home folder and rock on!

Hope this helps!

---

### Post by duanedesign on 2010-01-02
the sizes you have look pretty good. I set my / to 13 and I have 7.6GB of unused space. You could get away with 5gb, but if you have the space I would bump it up a bit. The 1 GB of swap looks good, as long as that is => the amount of RAM you have. The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size.

---

### Post by albert s on 2010-01-02
thanks guys, I'll go for the 15G for / ,  someone told me that I needed a mount point at the very beginning of every disc, I only have the one so I'll just leave it out.
Yes, I've only got 512 RAM.
reading through these threads, is there anything to be gained from 64bit,? I dont really do any major heavy work, its only a home desktop, I've pasted on the CPU info below,(I think)


ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping    : 2
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3590.25
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping    : 2
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3591.21
clflush size    : 64
power management:

---

### Post by Cheesemill on 2010-01-02
With only 512MB of RAM there is no real need for you to install 64-bit, you wont gain anything by it.

---

### Post by ratcheer on 2010-01-02
I use 1 GB for swap, 16 GB for /, 28 GB for /home, and 29 GB for /usr. This is for an 80 GB drive. I like having /usr as a separate partition, because it is where most software is installed.

Tim

---

### Post by noelvh on 2010-01-02
> **duanedesign said:**
> the sizes you have look pretty good. I set my / to 13 and I have 7.6GB of unused space. You could get away with 5gb, but if you have the space I would bump it up a bit. The 1 GB of swap looks good, as long as that is => the amount of RAM you have. The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size.

I just did an install with a 6g / and found I would run out of space soon. I have changed it to 10g for my / 45 for /home 3.9 /swap. The swap was a mistake and I will fix that soon.

Noel

---

### Post by Captain_tux on 2010-01-02
The use of a **/home** partition is highly recommended... you'll save yourself a ton of headaches when you upgrade.

---

### Post by albert s on 2010-01-02
thanks to everyone for their input,
I have done a 32bit install, 1G swap, 15G /  , and the rest for /home,  dont really understand the /usr  partition though, so I havent used one, did I really need this?
anyway, had a few other probs, will start a relevant thread with these, thanks again guys.  
:KS

---

### Post by Paqman on 2010-01-02
> **Cheesemill said:**
> With only 512MB of RAM there is no real need for you to install 64-bit, you wont gain anything by it.

That's not true. Any computationally intensive tasks like re-encoding video will be [a LOT faster in 64-bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1"). The downside is slightly bigger apps (both on the disk and in RAM) and the occasional 32-bit only package from 3rd parties.

---

### Post by tom.swartz07 on 2010-01-02
> **Paqman said:**
> That's not true. Any computationally intensive tasks like re-encoding video will be [a LOT faster in 64-bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1"). The downside is slightly bigger apps (both on the disk and in RAM) and the occasional 32-bit only package from 3rd parties.

well, you have to take into account the idea of his CPU. granted he said it was an older machine, and it only has 512mb of ram, he probably doesnt have a x64 processor. 

If he does, then so much the better. One doesnt start to see much of a difference until you go beyond 4gb of ram.

---

### Post by albert s on 2010-01-02
> **Paqman said:**
> That's not true. Any computationally intensive tasks like re-encoding video will be [a LOT faster in 64-bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1"). The downside is slightly bigger apps (both on the disk and in RAM) and the occasional 32-bit only package from 3rd parties.


I think the point was that as I only use my PC for general stuff I wouldnt see any benefit from 64 Vs 32 , and perhaps more probs (flash etc) than was outweighed.

---

### Post by Paqman on 2010-01-02
> **albert s said:**
> I think the point was that as I only use my PC for general stuff I wouldnt see any benefit from 64 Vs 32 , and perhaps more probs (flash etc) than was outweighed.

I just think there's a lot of misconceptions about 64-bit that get trundled out quite regularly on this forum. Being able to address 4GB+ of RAM is actually not the main benefit of 64-bit for most users. A faster system is.

Flash is fine on 64-bit these days. Especially if you use the native 64-bit Flash from Adobe.

I'd recommend switching to 64-bit nex t time you upgrade. Why throttle your chip down?

---

### Post by albert s on 2010-01-02
> **Paqman said:**
> I just think there's a lot of misconceptions about 64-bit that get trundled out quite regularly on this forum. Being able to address 4GB+ of RAM is actually not the main benefit of 64-bit for most users. A faster system is.

Flash is fine on 64-bit these days. Especially if you use the native 64-bit Flash from Adobe.

I'd recommend switching to 64-bit nex t time you upgrade. Why throttle your chip down?


Im not that computer savvy, thats why I posted my  CPUINFO  as I wasnt sure if 64 would even run on my specs.
anyway, I have more of a prob trying to sort my graphics out for now,,,,
:D

---

### Post by Paqman on 2010-01-02
> **albert s said:**
> thats why I posted my  CPUINFO  as I wasnt sure if 64 would even run on my specs.


Fair enough. Pretty much all CPUs made in the last few years (except for stuff like Atom chips in netbooks) are all 64-bit. Certainly all the Core2Duos are.

What's up with your graphics? If you've got an Nvidia card or integrated Intel you should be fine. For an ATI card you'll probably be best to use the drivers direct from AMD, not the ones in Hardware Drivers.

---

### Post by albert s on 2010-01-02
> **Paqman said:**
> Fair enough. Pretty much all CPUs made in the last few years (except for stuff like Atom chips in netbooks) are all 64-bit. Certainly all the Core2Duos are.

thanks Paqman, so do you really think it would benefit me to upgrade me to 64 bit for general use? I was gonna up the RAM to 1G but would that make any difference? I dont do gaming or anything like that, ripping music and research on the internet is about it, with the odd movie or video. thanks.

---

### Post by Paqman on 2010-01-02
> **albert s said:**
> thanks Paqman, so do you really think it would benefit me to upgrade me to 64 bit for general use?


I've used 64-bit for everything for years, and i'm completely happy with it. So i'd say yes.

> I was gonna up the RAM to 1G but would that make any difference?

Yep, whether you use 32- or 64-bit you'll have a _much_ better system at 1GB than 512MB. With 512MB you'd be hitting your swap pretty hard, which would slow you to a crawl if you had more than a couple of apps open.

>  
I dont do gaming or anything like that, ripping music and research on the internet is about it, with the odd movie or video. thanks.

64-bit will speed up ripping music and video, definitely. The rest of it will be same speed as 32-bit.

---

### Post by albert s on 2010-01-02
> **Paqman said:**
> I've used 64-bit for everything for years, and i'm completely happy with it. So i'd say yes.



Yep, whether you use 32- or 64-bit you'll have a _much_ better system at 1GB than 512MB. With 512MB you'd be hitting your swap pretty hard, which would slow you to a crawl if you had more than a couple of apps open.



64-bit will speed up ripping music and video, definitely. The rest of it will be same speed as 32-bit.


thanks paqman, have you looked at my cpuinfo and will 64 actually run on my system? 
if so then as soon as I get this prob sorted
[http://ubuntuforums.org/showthread.php?t=1370690](http://ubuntuforums.org/showthread.php?t=1370690)
 then Im gonna try it. thanks.

---

### Post by Paqman on 2010-01-02
> **albert s said:**
> thanks paqman, have you looked at my cpuinfo and will 64 actually run on my system? 


Yes. You have a Core 2 Duo E4300. All Core 2 Duos are 64-bit processors.

---

### Post by albert s on 2010-01-02
> **Paqman said:**
> Yes. You have a Core 2 Duo E4300. All Core 2 Duos are 64-bit processors.

thanks paqman,
maybe this is why Im so grateful that my original  old laptop finally crashed for the last time and brought me over to Linux, PEOPLE ACTUALLY HELP YOU and dont try to be mystical wizards.!
Im actually gonna try 64bit on this next week now that [Methuselah]("http://ubuntuforums.org/member.php?u=141554")  has gotten my graphics problem sorted.  :P:P:P

---

### Post by The Real Dave on 2010-01-02
Definately use a seperate /home partition. You'll save yourself so many headaches upgrading and re-installing. 
With an 80GB drive and a computer with 512Mb of RAM I would personally go with

8-10Gb / (ext4 for speed)
1Gb SWAP
and what ever you have left ~69Gb for /home, using ext3 for stability

I would advise however upgrading to 1Gb of RAM. 512Mb for Ubuntu isn't a lot, things run a lot faster with 1Gb as you'll probably rarely need to use your swap.

---

