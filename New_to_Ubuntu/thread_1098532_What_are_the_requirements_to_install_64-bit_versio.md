---
title: "What are the requirements to install 64-bit versions?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-03-17
for ubuntu and ultimate ubuntu

my system configuration is -
core2duo processor.
2.5 GB of RAM
17' CRT

---

### Post by Dynaflow on 2009-03-17
You need a 64-bit processor.  You have one.

---

### Post by Sethramoth on 2009-03-17
And you have more than enough RAM as well.

---

### Post by SunnyRabbiera on 2009-03-17
Yes your system will be able to run the 64bit version.
But do take note, a 64bit OS is not necessarily any major improvement over a 32bit one.
Granted a 64 bit kernel (the core of the OS) has the capacity to see more ram then a 32bit one (at least in the case of Linux)
But it doesnt offer any new graphics, any fancy features, its no different then a 32bit OS.
If you are running a 32bit system and it works stick with it, 32bit is not going anywhere right now.
The only real advantage of a 64bit kernel is the ability to use more ram

> **Sethramoth said:**
> And you have more than enough RAM as well.
Yes but he really doesnt need a 64bit kernel, he has less then 4 GB of ram

---

### Post by Sethramoth on 2009-03-17
> **SunnyRabbiera said:**
> Yes but he really doesnt need a 64bit kernel, he has less then 4 GB of ram

True, but by the same token he is not limited to a 32-bit operating system because he has less than 4GB RAM either, but having more certainly does make running a 64-bit operating system more justifiable.

---

### Post by presence1960 on 2009-03-17
> **eshant_engineer said:**
> for ubuntu and ultimate ubuntu

my system configuration is -
core2duo processor.
2.5 GB of RAM
17' CRT

Almost every CPU made today is 64 bit...what does that tell you? If you have a 64 bit CPU then maximize it's potential by using a 64bit OS. A lot of people will say there is no advantage just like people did when 16 bit & 32 bit came on the scene. It is human nature to resist change, but it comes nevertheless. I say use 64 bit!

---

### Post by hyper_ch on 2009-03-17
there's no reason anymore to not run 64bit nowadays...

you need a motherboard that can run 64bit and a cpu that can run 64bit.

---

### Post by jacksaff on 2009-03-17
You can run 32 bit applications using 64 bit linux.
'sudo apt-get install ia32-libs'

---

### Post by philinux on 2009-03-17
> **jacksaff said:**
> You can run 32 bit applications using 64 bit linux.
'sudo apt-get install ia32-libs'

There's even a 64 bit java plugin, beta, which I'm using. Very few 32 bit apps are needed now.

---

### Post by SunnyRabbiera on 2009-03-17
> **presence1960 said:**
> Almost every CPU made today is 64 bit...what does that tell you? If you have a 64 bit CPU then maximize it's potential by using a 64bit OS. A lot of people will say there is no advantage just like people did when 16 bit & 32 bit came on the scene. It is human nature to resist change, but it comes nevertheless. I say use 64 bit!

Well for his current specs there really isnt any advantage, if he/she got higher specs that changes.

---

### Post by eshant_engineer on 2009-03-17
I am confused because on Microsoft site i found there written that for running 64bit vista, ur system must have atleast 4GB of RAM. But does this requirement is also with Ubuntu flavours?

---

### Post by philinux on 2009-03-17
> **eshant_engineer said:**
> I am confused because on Microsoft site i found there written that for running 64bit vista, ur system must have atleast 4GB of RAM. But does this requirement is also with Ubuntu flavours?

I'm running 64 bit intrepid and 64 bit jaunty with 2 gig ram.

---

### Post by thehouseofho on 2009-03-17
The 4GB recommendation for 64-bit operating systems has more to do with giving users something they can easily view to see they are running a 64-bit operating system.  32-bit operating systems could not see 4GB of RAM.  The maximum amount of RAM a 32-bit operating system would show the user as available would be 3GB, while the other 1GB was dedicated to background system processes.

In 64-bit operating systems, you are able to install up to 32GB of RAM and view/allocate all 32GB.

---

### Post by philinux on 2009-03-17
> **thehouseofho said:**
> The 4GB recommendation for 64-bit operating systems has more to do with giving users something they can easily view to see they are running a 64-bit operating system.  32-bit operating systems could not see 4GB of RAM.  The maximum amount of RAM a 32-bit operating system would show the user as available would be 3GB, while the other 1GB was dedicated to background system processes.

In 64-bit operating systems, you are able to install up to 32GB of RAM and view/allocate all 32GB.

Some background reading.

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

32 bit systems can and have used pae to use more than 4 gig of memory and 64 bit max is in terabytes.

---

### Post by thehouseofho on 2009-03-17
> **philinux said:**
> Some background reading.

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

32 bit systems can and have used pae to use more than 4 gig of memory and 64 bit max is in terabytes.

Yes, using PAE you can get up to 64GB of addressable memory on 32-bit and up to 2TB on 64-bit operating systems, but I would say 99% of users wouln't enable PAE.  Whether you're using AWE (on Windows) or mmap (on *nix systems), mapping page tables to processes is pretty tedious and requires upkeep.

That's a lot of work for a standard user, no matter what platform they run.

---

### Post by Skol312000 on 2009-03-17
Is it hard or different to run 32 bit aplications on 64 bit ubuntu version?  Is installing any different?

How do i find 64 bit only apps or 32 bitonly apps


How do i know an app is 64 bit or 32 bit?   Please help?

Im fixing to switch my os to 64 bit!!

---

### Post by philinux on 2009-03-17
> **Skol312000 said:**
> Is it hard or different to run 32 bit aplications on 64 bit ubuntu version?  Is installing any different?


I'm on 64 bit intrepid now, I just use synaptic. ia32-libs is installed by default so everything is taken care of.

Which apps in particular?

---

### Post by jms1989 on 2009-03-17
I run ubuntu 32bit on my quad core with 8 gigs of ram using the latest server kernel for ubuntu and I can see all 8gigs. I find there to be more compatibility with 32bit OSes then there is with 64 bit OSes.

Would there be any performance boosts by using a 64bit os when compared to a 32 on a quad core?

---

### Post by mcduck on 2009-03-17
> **jms1989 said:**
> I run ubuntu 32bit on my quad core with 8 gigs of ram using the latest server kernel for ubuntu and I can see all 8gigs. I find there to be more compatibility with 32bit OSes then there is with 64 bit OSes.

Would there be any performance boosts by using a 64bit os when compared to a 32 on a quad core?

That depends on what you use your computer for.

Most common apps that benefit from 64-bit OS are different image processing, audio and video applications (as long as the program really is made to use 64 bits).

For more "normal" desktop tasks the only benefit from 64 bits is the higher memory limits without the extra latency in memory access you get when using PAE. Of course for most of normal desktop tasks there isn't any need for much memory either..

In other words, support for more RAM is just one of the benefits of 64-bit computing, but you need to do something that actually benefits from 64 bits before you get any performance boost.

---

### Post by oldos2er on 2009-03-17
> **Skol312000 said:**
> Is it hard or different to run 32 bit aplications on 64 bit ubuntu version?  Is installing any different?

How do i find 64 bit only apps or 32 bitonly apps


How do i know an app is 64 bit or 32 bit?   Please help?

Im fixing to switch my os to 64 bit!!

It isn't difficult to run 32-bit apps on 64-bit Ubuntu. The package managers behave exactly the same on both versions as well. When you install 64-bit Ubuntu, it automatically sets itself to install packages from the 64-bit repositories, just as the 32-bit version does with the 32-bit repositories.

 To find out the bitness of an executable, use the "file" command:
```
ann@ann-desktop:/usr/bin$ file expiry
expiry: setgid ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
``` for example.

 Visit the x86_64 subforum for more info.

---

