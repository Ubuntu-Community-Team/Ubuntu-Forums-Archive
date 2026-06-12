---
title: "Change from 32-bit to 64-bit on existing installation."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by fjf314 on 2008-12-04
Hi everyone! I've been using Ubuntu since 6.06 but this is my first foray into using it with a 64-bit processor. Just tonight I put Ubuntu 8.10 on my Dell Inspiron 1526 with an AMD Turion 64 processor. I ran uname -a and got the following:

Linux ubuntu-tan 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

So I'm running the 32-bit version. Is there any way I can upgrade that to the 64-bit version while keeping my current installation?

Thanks in advance to anyone who can give me a heads-up with this!

---

### Post by ByteJuggler on 2008-12-04
In short, no.  There's no *direct* upgrade path.  However, it might be possible to, without *that* much trouble, save the package list of all the packages you have installed, back up all your data, do a clean installation of 64-bit ubuntu, restore your home folder and re-install the packages from your package list.  Which should give you mostly the same as what you want.

---

### Post by fjf314 on 2008-12-04
Thanks for the speedy heads up on this!

I didn't really think it would be terribly difficult to do a fresh installation and then restore what I have, I just figured I would check for sure.

Thanks again!

---

### Post by Skripka on 2008-12-04
Also, unless you have 4Gb or more RAM, you won't really be gaining that much.

---

### Post by fjf314 on 2008-12-05
Oh really? I wasn't sure if there were any real benefits... I just figured that if I have a 64 bit processor I may as well use a 64 bit OS with it. That said, I only have 3 GB of RAM, so I don't have enough where I need to worry about x86 systems not being able to recognize all of it. I haven't yet done a fresh install, so I might just stick with the x86 version for awhile if it won't make much of a difference. Thanks for letting me know!

---

### Post by ByteJuggler on 2008-12-05
Agreed, unless you have more than 3GB or RAM, you might as well stay with 32bit.  Dont fix it if it ain't broke!

---

### Post by fjf314 on 2008-12-05
2 people sounds like enough for a healthy verdict to me. I'll just stick with the x86 versions instead of bothering to do another installation since I won't be getting much out of it.

Thanks again for the input.

---

### Post by Paqman on 2008-12-05
Next time you do install, you might as well use the 64-bit though. There's no reason not to use it, really.

---

### Post by oldos2er on 2008-12-05
I won't ever go back to 32-bit, just because I enjoy using my hardware to its fullest capacity. There's nothing I did on 32-bit that I can't also do on 64-bit.

---

### Post by fjf314 on 2008-12-06
I certainly agree with the both of you. When Jaunty releases I'll probably go ahead and do a clean install with the x86_64 version of it, even if for no better reason than because I can. I'm just not going to bother needlessly doing away with my current Intrepid installation for no real gain.

---

### Post by Chris Watts on 2008-12-06
I am having trouble understanding this memory thing everyone in the forums is saying. What has the 64 bit untilisation of a CPU got to do with memory usage. Also, wouldn't the CPU be transferring 64 bits (8 bytes) of data to or from RAM in each clock cycle as opposed to only 4 bytes for a 32 bit kernel, not to mention the internal cache should theoretically copy data at twice the speed ? I currently use an intel Core Duo (with 2Gb RAM) with 64bit Ubuntu and the only grievance I have had is the lack of GUI drive management tools and the lack of 64bit flash player support which as of yesterday has been fixed anyway.... I personally think the memory argument is not based on any scientific reasoning... but if someone can explain it and back their explanation up with reliable references I will stand corrected.

---

### Post by Skripka on 2008-12-06
> **Chris Watts said:**
> I am having trouble understanding this memory thing everyone in the forums is saying. What has the 64 bit untilisation of a CPU got to do with memory usage. Also, wouldn't the CPU be transferring 64 bits (8 bytes) of data to or from RAM in each clock cycle as opposed to only 4 bytes for a 32 bit kernel, not to mention the internal cache should theoretically copy data at twice the speed ? I currently use an intel Core Duo (with 2Gb RAM) with 64bit Ubuntu and the only grievance I have had is the lack of GUI drive management tools and the lack of 64bit flash player support which as of yesterday has been fixed anyway.... I personally think the memory argument is not based on any scientific reasoning... but if someone can explain it and back their explanation up with reliable references I will stand corrected.

Memory addressing is a common way of simplifying the differences.  32-bit can only adress an *absolute* ceiling of 4 GB (which becomes 3.2 GB after a a few caveats); AMD64 can actually only address 40-bit addresses (an absolute ceiling around 1TB). In all honesty-few programs exist out there which really take advantage of 64-bit processing, and even fewer take advantage of modern multiple-core processors.


[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

The sticky over in X86_64 forum

Also:

[http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1)


I've found that some things run just fine under wine on an i386 distro, and don't run at all under amd64.  With 64-bit flash out natively that is the other major annoyance.

---

### Post by gn2 on 2008-12-06
> **Skripka said:**
> Also, unless you have 4Gb or more RAM, you won't really be gaining that much.

Not so. [This story]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1") has benchmark tests which suggest there is benefit to be had from using 64-bit.

As for RAM, Linux isn't Windows, 32-bit Linux can be made to use up to 64gb of RAM.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Paqman on 2008-12-06
> **gn2 said:**
> 
As for RAM, Linux isn't Windows, 32-bit Linux can be made to use up to 64gb of RAM.


Indeed. The whole 4GB barrier can be broken by any kernel compiled to do so. It's not an absolute limit on Linux.

I believe there's a limit of 4GB per process, but how many desktop systems run processes that could suck up 4GB?

---

### Post by fjf314 on 2008-12-06
> **gn2 said:**
> Not so. [This story]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1") has benchmark tests which suggest there is benefit to be had from using 64-bit.

As for RAM, Linux isn't Windows, 32-bit Linux can be made to use up to 64gb of RAM.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Wow... I didn't know about either of these points. I just assumed x86 was x86 regardless of OS. Thanks for the great information here. And looking at those x86 vs. x86_64 comparisons, I might have to reconsider my decision once again.

---

### Post by ByteJuggler on 2008-12-06
> **gn2 said:**
> Not so. [This story]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1") has benchmark tests which suggest there is benefit to be had from using 64-bit.

As for RAM, Linux isn't Windows, 32-bit Linux can be made to use up to 64gb of RAM.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Windows 32-bit can also be made to use more than 4GB using PAE, same way as Linux, but it's an equally bad idea IMHO.  This is NOT just a software/OS issue as some seem to try to make out!  You really must understand, except for *hacks* like PAE, 32-bit addressing ***limits ***you to 4GB of address space! It's really that simple! A 32-bit CPU (or a 64-bit CPU running in 32-bit mode) has 32 lines with which to adress a memory byte.  This means it can address up to 4GB of RAM.  Which is why you *either* need a hack using some form of paging (like PAE) or proper 64bit addressing (which enlarges your address space by in principle using 64 address lines to address a byte) to properly utilise more than 4GB of RAM.  And in any case, with PAE (which is a hack) you're nevertheless still limited to no more than 4GB or RAM per process.  So, for example, if you have a massive database, and 16GB of RAM, then your database server process will not be able to make use of more than 4GB of your RAM in its single process space.   Lovely (not).

---

### Post by ByteJuggler on 2008-12-06
> **Paqman said:**
> Indeed. The whole 4GB barrier can be broken by any kernel compiled to do so. It's not an absolute limit on Linux.

I believe there's a limit of 4GB per process, but how many desktop systems run processes that could suck up 4GB?

Gaming rigs, certainly.  And try using some heavy processing on things like Adobe Photoshop.  It can use all the RAM it can get its hands on.

---

### Post by ByteJuggler on 2008-12-06
> **gn2 said:**
> Not so. [This story]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1") has benchmark tests which suggest there is benefit to be had from using 64-bit.

As for RAM, Linux isn't Windows, 32-bit Linux can be made to use up to 64gb of RAM.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Yes, there is ***a*** benefit, which is what the original poster already said, but in practice, it's not hugely massive.  It really does depend on the application.   However, nevertheless run 64-bit if you can by all means.

---

### Post by ByteJuggler on 2008-12-06
The issue is well explained in [this article]("http://techfiles.de/dmelanchthon/files/memory_hole.pdf") as well, so I thought I'd post the link.  I quote:

> PAE availability doesn&#8217;t eliminate 4 GB limitation. On the contrary, it raises other 32-bit problems. The largest is that all software must explicitly program for and use the PAE extensions. This will affect applications, operating systems, hardware device drivers and hardware itself. Software is still running in 32-bit mode, not 36/40 bit mode and registers and native data types are still 32 bits.

---

### Post by 3rdalbum on 2008-12-06
On Windows, PAE is an especially bad idea. You need drivers that have been written with PAE in mind, and on Windows these are rarer than 64-bit drivers!

I haven't noticed any speed improvements with 64-bit, but this may be different if a program is rewritten for EMT64 and AMD64. I don't see that the difference could be more than what you can accomplish by overclocking your CPU with its stock cooler. Certainly, running 64-bit Linux is no more difficult than running 32-bit.

---

### Post by gn2 on 2008-12-07
> **ByteJuggler said:**
> Yes, there is ***a*** benefit, which is what the original poster already said, but in practice, it's not hugely massive.  It really does depend on the application.   However, nevertheless run 64-bit if you can by all means.

I agree. 
The size of the benefit depends on the application(s) in use and the job to which it's (they're) being put.

If you have a 64-bit capable CPU there's no reason to stick with 32-bit Ubuntu (that I can think of) these days.

---

