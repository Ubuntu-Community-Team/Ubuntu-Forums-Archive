---
title: "Memory Issue"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by TAspr on 2011-03-09
Hello folks!

I originally had 2GB of memory installed, then installed 6GB, and this was my result;

Is it not recognising the memory?  I originally had 2 GB installed which worked fine with the original memory as well as an additional 2, 2GB sticks, which made it a total of 6GB.

[U][B]Total after 6GB memory
[/B][/U]
PC:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          3465        678       2786          0         52        315
-/+ buffers/cache:       311       3154
Swap:         5960          0         5960
Total:          9426        678       8747


PC:~$ lshw -C memory
  *-memory                
       description: System memory
       physical id: 0
       size: 3465MiB

[B]Pass 2 after taking the third Dimm out
****************************************[/B]

PC:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          3489        435       3054          0         47        191
-/+ buffers/cache:        196       3292
Swap:         5960          0       5960
Total:        9450        435       9015


PC:~$ lshw -C memory
  *-memory                
       description: System memory
       physical id: 0
       size: 3489MiB
PC:~$ 



What gives, do I have to have matching pairs?

---

### Post by turtle153 on 2011-03-09
You're probably on a 32 bit system. A 32bit system can only assign 2^32 (4294967296) bits of memory, which is 4GB. You're showing 3.4GB, which suggests its 32bit.

---

### Post by doas777 on 2011-03-09
> **turtle153 said:**
> You're probably on a 32 bit system. A 32bit system can only assign 2^32 (4294967296) bits of memory, which is 4GB. You're showing 3.4GB, which suggests its 32bit.
post back the output of 
```
uname -a
``` if you would like us to confirm.

---

### Post by TAspr on 2011-03-09
Well, why wouldn't my system be 64 bit?  I am not sure if Linux is a 64 or 32 bit, but I am running Linux.

---

### Post by TAspr on 2011-03-09
PC:~$ uname -a
Linux user-PC 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 
UTC 2011 i686 GNU/Linux
PC:~$

---

### Post by doas777 on 2011-03-09
yup, thats 32 bit.

---

### Post by scrooge_74 on 2011-03-09
you needed to install the amd64 version. You are running a 32 bit system so you are not taking advantage of all that memory increase

Sorry

---

### Post by TAspr on 2011-03-09
So, another words, I can't upgrade the memory because it is 4GB?  What if I put in 8GB?

---

### Post by doas777 on 2011-03-09
> **TAspr said:**
> So, another words, I can't upgrade the memory because it is 4GB?  What if I put in 8GB?
best case: the system works fine but ignores the ram above 3.8GB.
worst case: the system will not boot.

there is no way to get past the 4GB boundary if you are running 32bit.

---

### Post by TAspr on 2011-03-09
What tells you it is a 32 bit?

---

### Post by cascade9 on 2011-03-09
> **TAspr said:**
> PC:~$ uname -a
Linux user-PC 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 
UTC 2011 i686 GNU/Linux
PC:~$

i686 (and i386, i486, i586 as well) is 32bit. 


> **doas777 said:**
> there is no way to get past the 4GB boundary if you are running 32bit.

Yeah, there is, a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

You should be able to install the PAE kernel from software centre, or synaptic. 

PAE is a bit of a hack, I'd rather use 64bit myself. But at least if you install the PAE kernel you wont have to reinstall to see all your RAM.

---

### Post by doas777 on 2011-03-09
> **TAspr said:**
> What tells you it is a 32 bit?
the '686' token in uname -a.
if it was 64bit it would be somthing like
'EMT 86/64' (just off the top of my head. somthing like that.)

---

### Post by TAspr on 2011-03-09
> **cascade9 said:**
> i686 (and i386, i486, i586 as well) is 32bit. 




Yeah, there is, a PAE kernel. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

You should be able to install the PAE kernel from software centre, or synaptic. 

PAE is a bit of a hack, I'd rather use 64bit myself. But at least if you install the PAE kernel you wont have to reinstall to see all your RAM.


So, do you think by installing the PAE kernal, it would see all my ram and perform as well?

Which ones should be installed, the back-ported drivers, the Linux drivers, Ubuntu Supported drivers, Header files?

---

### Post by turtle153 on 2011-03-09
It also depends if you have a 64bit CPU. Can you post the output of ```
lscpu
```

> 'EMT 86/64' (just off the top of my head. somthing like that.)
x86_64 for 64bit, at least on my AMD

---

### Post by bodhi.zazen on 2011-03-09
> **TAspr said:**
> So, do you think by installing the PAE kernal, it would see all my ram and perform as well?

Which ones should be installed, the back-ported drivers, the Linux drivers, Ubuntu Supported drivers, Header files?

You can either :

1. Try the PAE kernel.

2. Install 64 bit Ubuntu.

I have used the PAE kernel and in general it works well.

My advise would be to use 64 bit Ubuntu as you have a 64 bit CPU and fall back to 32 bit Ubuntu with PAE in the unlikely event you have problems with 64 bit Ubuntu.

---

### Post by migs73 on 2011-03-09
As Turtle says above, if it returns it's 64 bit capable it'll run the PAE kernel. To install it follow this;

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Then enjoy all your RAM!!

I would install the 64bit version when you have the opportunity.
 

Mike

---

### Post by jerome1232 on 2011-03-09
> **TAspr said:**
> PC:~$ uname -a
Linux user-PC 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 
UTC 2011 [COLOR="Red"]i686[/COLOR] GNU/Linux
PC:~$

The part in red, i386, i486, i586, and i686 are all 32-bit. You need to download and install the 64-bit version if you want to use > 4 GB's of ram. This is True on all Operating Systems.

And I thought the PAE Kernel had disadvantages.

edit: Weird When I checked this thread I didn't see all the replies even though they say there were from 15+ minutes ago....

---

### Post by cascade9 on 2011-03-10
> **jerome1232 said:**
> The part in red, i386, i486, i586, and i686 are all 32-bit. You need to download and install the 64-bit version if you want to use > 4 GB's of ram. This is True on all Operating Systems.

And I thought the PAE Kernel had disadvantages.

*blinks* Err..if you know about PAE you know that you do not need to use 64bit to see and use all teh RAM. 

PAE does have disadvantages, its slower than 64bit (and depending on what you want to believe, its slower than normal 32bit) and you are limited to 3/4GB of RAM for any single process.

---

### Post by JKyleOKC on 2011-03-10
> **TAspr said:**
> What tells you it is a 32 bit?The "i686" in the result of uname.

It's possible to extend the RAM to the full 4 GB by using a "PAE" kernel, but not possible to go past that point for the same reason that you can't count to 10 using only single digits: when you pass 9 you have to use a second digit, and in memory when you pass 4 GB you have to have 33 or more bits to address it. Actually that happens when you hit 4 GB, but since the addressing starts at 0 rather than at 1 this cancels out.

The 64-bit versions have a slightly misleading name of "AMD64" but they work with Intel processors also; the name comes from AMD having been the first to get a working 65-bit chip to market.

If your computer can handle 64 bits your best bet will be to back up all your data and then do a clean install of the 64-bit Linux of your choice. Most any machine made during the past 5 years or so will be 64-bit capable.

---

### Post by cascade9 on 2011-03-10
> **JKyleOKC said:**
> It's possible to extend the RAM to the full 4 GB by using a "PAE" kernel, but not possible to go past that point for the same reason that you can't count to 10 using only single digits: when you pass 9 you have to use a second digit, and in memory when you pass 4 GB you have to have 33 or more bits to address it. Actually that happens when you hit 4 GB, but since the addressing starts at 0 rather than at 1 this cancels out.

Umm, no. And heres a screenshot- 

[IMG]http://members.apex-internet.com/sa/windowslinux/images/linux_pae_memory.gif[/IMG]

[http://members.apex-internet.com/sa/windowslinux/images/linux_pae_memory.gif](http://members.apex-internet.com/sa/windowslinux/images/linux_pae_memory.gif)

i686 PAE, 5.9GB RAM. Or GiB if you perfer.

No, its not mine, just a ramdom find on the net. 

There is a limit to how much RAM any single process can use (3/4GB like I said about), but you can see and use more than 4GB with PAE. 

An explanation here- 

[http://randosity.wordpress.com/2009/01/30/so-you-want-8gb-of-ram/](http://randosity.wordpress.com/2009/01/30/so-you-want-8gb-of-ram/)

---

### Post by migs73 on 2011-03-10
Oops---Ignore this!!!

---

### Post by micasper on 2011-04-02
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

