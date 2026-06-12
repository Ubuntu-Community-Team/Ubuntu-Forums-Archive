---
title: "32bit or 64bit?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by fantab on 2011-05-03
I have used Ubuntu 10.10 32bit for a month along with Windows 7 32bit. Now I want to move to 11.04 and I have decided to make a clean install. 

I want to install 11.04 64bit on a separate HDD which I recently added to my Desktop. 

My doubts are:

*** Should I download and install 32bit or 64bit?** I have the following hardware Config:

Processor - Intel Core 2 Duo E8400 (it is a 64 bit processor)
Ram - Corsair 2Gb DDR2 800mhz.
Desktop Board - Intel DG45ID (Media Series).
HDD - 1. 500GB (for Windows) and 2. 1TB (for Ubuntu and General Storage)

I am NOT using Windows 7 64bit because I was informed that I need at least 4GB of Memory for 64bit Windows. Hence I am currently using Windows 7 32bit.

**Does Ubuntu 11.04 64bit too require more than 2GB Memory RAM to run?** 
**If YES**, then how much more memory do I need?

And **if NO**, then will it affect in any way to use Windows 32bit and Ubuntu 64bit? I ask this because I will be using Windows and will need and use my media files from the Windows HDD as well. 

Also when I download the 11.04 64bit the file says ubuntu-11.04-desktop-amd64.iso, is this compatible with Intel? I have this doubt because it says **amd64**.

I Request the forum to clear my doubts.

---

### Post by 3rdalbum on 2011-05-03
> **fantab said:**
> 

**Does Ubuntu 11.04 64bit too require more than 2GB Memory RAM to run?** 

No, certainly not. My system is currently using 1.1 GiB of RAM and it's 64-bit and running a couple of programs.

> And **if NO**, then will it affect in any way to use Windows 32bit and Ubuntu 64bit?

Not at all. They will run as normal, and the CPU will automatically switch modes from 32-bit to 64-bit and vice-versa as required.

> Also when I download the 11.04 64bit the file says ubuntu-11.04-desktop-amd64.iso, is this compatible with Intel?

Yes it is. It's called AMD64 because AMD invented the 64-bit extensions for the x86 CPUs. Intel's CPUs use AMD64, so you can use an AMD64 operating system on an Intel CPU just as I am currently doing :-)  In short, yes that's the most applicable download for you.

---

### Post by Crillius on 2011-05-03
ok, I might be new at this, but why do you want to switch to the 64bit version?

-- Ubuntu Community, correct me if I'm wrong here. --

As far as I know, 64bit versions of Windows Operating Systems are pretty much only usefull if you have 4GB of RAM or more in your system and wish to make use of all of it, seeing as the 32bit versions only recognise 3,2GB or something in that ballpark.
I have also heard that the 64bit version eats more RAM then the 32bit one, but I doubt W7 64bit actually "requires" at least 4GB, it's just that having 4GB is kinda useless if you run the 32bit version.

If I recall correctly, I read somewhere on these forums that the 32bit version of Ubuntu can and will support up to 4GB of RAM, in essence making the 64bit kinda abundant.

I do realise there are 64bit applications out there, but sofar I have heard very little, and they seem to be rare.

I don't know how the 32bit or 64bit OS will communicate with your CPU, as you mention it is a 64bit processor. I'll leave that to the experts.
Actually, that might be nice to know for myself, as i have a Pentium Q6600 quad core, with 3BG of RAM, not sure if that CPU is 64bit tho.

The experts may answer that part: does a 64bit OS communicate with the CPU in  such a way that the processor's capabilites are used to a greater extent?

Just my two cents.

---

### Post by fantab on 2011-05-03
> **3rdalbum said:**
>  In short, yes that's the most applicable download for you.

Thanks a lot for your clarifications **3rdalbum**.

I will move ahead and install 11.04 64bit... and if at all any problems I can always go back to 32bit.

Regards...

---

### Post by oldos2er on 2011-05-03
> **Crillius said:**
> 
I do realise there are 64bit applications out there, but sofar I have heard very little, and they seem to be rare.

The 64-bit repositories are full of them. :)

---

### Post by Crillius on 2011-05-03
64bit repositories...obviously... are those just 64bit versions of regular 32bit progs n stuff?

Was the rest of my post anything near accurate tho?

---

### Post by oldos2er on 2011-05-03
Your processor appears to be 64-bit, if it's Intel Core 2 Quad Processor Q6600 (not "Pentium"). You can check by running **cat /proc/cpuinfo**, and check for the 'lm' flag. My general advice is, if you have a 64-bit CPU, run 64-bit Ubuntu.

---

### Post by oldfred on 2011-05-03
I run 64 bit on both my Desktop with 4GB of RAM and my laptop with 1.5GB of RAM so I have the same configuration for both.

Some have said the cross over point for increased RAM usage of 64bit and faster speed of 64 bit is about 2GB of RAM. So my 1.5GB may not be optimal but it works.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

---

### Post by alphacrucis2 on 2011-05-03
There could be a performance enhancement with 64bit for heavy duty computational stuff like video transcoding. I have never bothered with 32bit. Originally 64 bit did cause some grief with Adobe's proprietary flash which was 32 bit only and required installing a bunch of the 32 bit libs to make to work. That issue was sorted out a while ago with adobe releasing a proper 64 bit version.

---

### Post by 3rdalbum on 2011-05-03
> **Crillius said:**
> 

If I recall correctly, I read somewhere on these forums that the 32bit version of Ubuntu can and will support up to 4GB of RAM, in essence making the 64bit kinda abundant.

32-bit ANY operating system will recognise up to 4 GiB of total system memory, but this includes memory that is not part of your main RAM (for instance, graphics card memory, SATA and USB buffer, sound buffer etc). In other words, 3.3 GiB or less of your RAM addressable. If you run a 64-bit operating system, you can have 4 GiB of RAM usable and all the rest of the memory usable too.

> I do realise there are 64bit applications out there, but sofar I have heard very little, and they seem to be rare.

One of the advantages of open-source Linux software is that you can simply recompile it for 64-bit, or for a completely different CPU architecture. The Ubuntu developers have done the recompiling for you - anything in the 32-bit repositories is also in the 64-bit repositories, usually as a native 64-bit binary.

---

### Post by Automat2 on 2011-05-03
I use 64-bit Ubuntu on my Quad core AMD and 4GB RAM.

I think is only on certain occasions where 64-bit architecture presented problems, and I had to use 32-bit config. I am talking about Flash and apps that used Flash on Maverick Meerkat (10.10).

Now am using Natty (11.04), still at 64-bits. Some of these problems have disappeared from install, surely due to the hard work of the developers.

---

### Post by Grone1985 on 2011-05-03
I haven't used a 64bit version in a long time and I remember there were some issues with different programs. How is that going now? I have a new laptop, a Samsung RV411 with 2 GB RAM and an Intel Core i3 processor.

Thanks!

---

### Post by scott-ian on 2011-05-03
Most Linux programs are available for 64 bit.

---

### Post by Grone1985 on 2011-05-05
Besides the program availability, are there still any expected issues with the 64bit version like there used to be?

On the other hand, what are the benefits from using the 64bit version? I have a Samsung laptop with an Intel Core i3 processor and 2GB of RAM. I want to use it with UbuntuStudio to record from my guitar an things like that.

---

### Post by oldos2er on 2011-05-05
Some of this is a bit dated, but mostly relevant: [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

