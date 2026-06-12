---
title: "HELP!  3 Questions from a Semi-newbie"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Zenrunner92 on 2010-09-14
..."Semi" in that I was happily using a laptop with Ubuntu Debian that a friend installed for me, for about 2 months before he moved away and the laptop went with him.  Currently I am running Linux Mint on a Samsung NC10 netbook, which is not working too well (perhaps due to the NC10's limitations) so I will soon put Ubuntu for Netbooks on it.  

But I'm asking more for advice about my new Asus UL50 (Intel Core 2 Duo SU7300(1.30GHz) 4GB DDR3 / 500GB HDD / NVIDIA GeForce G210M / Win7 Premium 64 bit) laptop which just arrived today:

1.  Is a dual-boot system (Win7 + some form of Ubuntu) any slower or less stable than a single-OS system?  At present I am planning on a dual boot system so that I can do secure web browsing in Ubuntu and resolve any compatibility issues by going back to Windows, unless there are strong advantages in having only one OS.

2.  Which Ubuntu or Linux distro would you recommend for a non-power user like myself?  I do zero gaming or programming or video editing.  Only use internet, office apps, downloading, and music/videos.  

I do not need any flashy graphics interface, no cutesy bells and whistles --- just want something that's really easy to use (I have no experience with typing in command lines), lean, fast and stable.  

In my Googling I have found 3 distros that caught my eye: Fluxbuntu, Freespire, and gOS with Fluxbuntu reputedly the leanest and fastest, but am wondering how easy to use it is.  Am also wondering if Mint will run much better on my Asus than on the Samsung where it often slows or hangs; I do like the fact that it already comes with all the audio/video codecs I need.  I guess I could go back to the Ubuntu Debian that I had on my friend's laptop but I kind of dread having to find and install the needed codecs.

3. And finally, is there a website that facilitates getting all the needed hardware drivers for specific computer makes and models for each distro?  For example, on my Samsung netbook, after installing Mint most of my FN key functions no longer work, most annoyingly the brightness controls.  

Overall I really like the Linux/Ubuntu OS, but do find it very intimidating for a recovering English major like myself.  : )


Thanks for your help!
ZR

---

### Post by TonKi on 2010-09-14
> **Zenrunner92 said:**
> 

1.  Is a dual-boot system (Win7 + some form of Ubuntu) any slower or less stable than a single-OS system?  At present I am planning on a dual boot system so that I can do secure web browsing in Ubuntu and resolve any compatibility issues by going back to Windows, unless there are strong advantages in having only one OS.

No.

> 2.  Which Ubuntu or Linux distro would you recommend for a non-power user like myself?  I do zero gaming or programming or video editing.  Only use internet, office apps, downloading, and music/videos.

Ubuntu - of course (LTS 10.04)

> 3. And finally, is there a website that facilitates getting all the needed hardware drivers for specific computer makes and models for each distro?  For example, on my Samsung netbook, after installing Mint most of my FN key functions no longer work, most annoyingly the brightness controls.

The [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks") is a good start

---

### Post by Zenrunner92 on 2010-09-14
TonKi,

Thanks for replying so quickly.  

The Ubuntu download page says that the 64-bit download is "Not recommended for daily desktop usage" --- huh?  I was told that if I were running the 32-bit version, it would not be able to fully use all 4GB of memory my laptop has...true or no?

What are the pros and cons of using the 32 bit vs. the 64 bit on a 64 bit machine?

---

### Post by Zill on 2010-09-14
> **Zenrunner92 said:**
> ...I was told that if I were running the 32-bit version, it would not be able to fully use all 4GB of memory my laptop has...true or no?

What are the pros and cons of using the 32 bit vs. the 64 bit on a 64 bit machine?
Zenrunner92 - You said
> ...a non-power user like myself? I do zero gaming or programming or video editing. Only use internet, office apps, downloading, and music/videos...
IMHO 32-bit is fine for your usage - you are unlikely to ever use *all* 4GB. ;-)

---

### Post by fly-by-night on 2010-09-14
No codecs needed for audio/video.  VLC media player plays just about anything you throw at it.

---

### Post by Zenrunner92 on 2010-09-14
> **Zill said:**
> IMHO 32-bit is fine for your usage - you are unlikely to ever use *all* 4GB. ;-)

Yes I figured that I was already buying a lot more computing power than I actually needed, lol.  

Still, am just curious if that means that the 64 bit version would actually run more slowly or less stable on that machine?  Seems kind of strange, I would've thought the exact opposite.  

Off topic: does that mean that a 32 bit version of Win7 would also run better on a 64 bit machine than the 64 bit version of Win7?

---

### Post by Zenrunner92 on 2010-09-14
> **fly-by-night said:**
> No codecs needed for audio/video.  VLC media player plays just about anything you throw at it.

Huh, I thought that was true only for the Windows version of VLC...my friend said something about copyright or legal issues was involved in the case of Ubuntu.

---

### Post by Jazzy_Jeff on 2010-09-14
Most of the problems people have with the 64 bit version has to do with flash. Adobes flash support is not the greatest in Linux. There are ways to make it work though. I currently use 64 bit Ubuntu and I love it. It is very fast and for me very stable. If all your doing is pretty much light use then the 32 bit or 64 bit version will work well for you. I don't think you would even notice the difference.

---

### Post by 3Miro on 2010-09-14
64-bit Windows and Ubuntu both run faster than the 32-bit equivalents. The speedup depends on the application that you are using. In both cases there are occasional compatibility issues, such as flash and some codecs, however, in both cases they can be resolved easily. I have been running 64-bit Linux for couple of years now and I don't see any reason not to do it.

1. In a dual-boot system the Linux and Windows coexist separately on the hard-drive and only one is running at a time. There are no "stability" issues, just the potential of running out of HDD space.

2. For someone with absolutely no experience, plain Ubuntu 10.04 is probably the best. Get the basics there and then you can move to other distros. In my experience, Ubuntu is very Gnome-centric and thus the Ubuntu spinoffs tend to be less stable.

3. The vast majority of drivers are already in the Linux kernel so you don't have to download anything. The few exceptions like proprietary ATI and NVIDIA, some printers and Broadcom wireless are packaged for individual distribution, by the people making the distribution. Ubuntu is the most robust in that respect, since you get Hardware Manager that does everything automatically for you, other distros usually require more effort.

---

### Post by Zenrunner92 on 2010-09-14
> **3Miro said:**
> 64-bit Windows and Ubuntu both run faster than the 32-bit equivalents. The speedup depends on the application that you are using. In both cases there are occasional compatibility issues, such as flash and some codecs, however, in both cases they can be resolved easily. 

Thanks so much for your detailed answers, that's extremely helpful!  

So do you think that the fairly basic apps that I'll be using (Firefox, VLC, Quod Libet, Open Office, Transmission, Skype) will show any noticeable performance gains when run off the 64 bit version of Ubuntu?

---

### Post by Lateralis on 2010-09-14
Those apps will not increase in speed when using the 64-bit edition.  

Also in my own personal experience, the 64-bit version of either Windows or Linux aren't that much faster than their 32-bit equivalents.  

If all you're doing is pretty routine, basic stuff, the 32-bit edition will be absolutely fine.

---

### Post by 3Miro on 2010-09-14
Skype is proprietary and 32-bit only. The 64-bit Skype installer, installs 32-bit Skype on a 64-bit machine. There is nothing to gain there.

OpenOffice will depend on the size of the documents that you are working on. If you get something with hundreds of pages, then you may get performance boost, otherwise it will be negligible. 

If you want to speed up FireFox, use Google-Chrome or Opera. Firefox project is more Windows oriented and it works slow under Linux.

Transmission depends on the HDD, which is bit independent and sound players take almost no resources anyway.

VLC is the only thing that may improve if you are watching movies in very high resolution that require a lot of decoding.

Benchmarks put the 64-bit advantage for every day use around 10%, coding/decoding and compiling programs are the main things where you may get significant improvement.

---

### Post by Lateralis on 2010-09-14
> **3Miro said:**
> 
If you want to speed up FireFox, use Google-Chrome or Opera. Firefox project is more Windows oriented and it works slow under Linux.


Funny actually.  I always thought FF was slow in Linux, up until the last year.  I've had no issues with FF at all - runs quickly and efficiently for me on both my home desktop and laptop.  In fact, I generally find Opera to be slower than FF.  

I have not used Chrome on Linux, but found Chrome on Windows to have an interface which annoyed the hell out of me.  But that's personal taste. :) 

Anyway... I should stop blabbing about browsers!  I guess my point was: I find FF OK - chose whichever browser you like and get on with.  :)

---

### Post by Zenrunner92 on 2010-09-14
OK, I think I'll go with the 32 bit version then ... a 10% performance difference doesn't seem worth having to deal with possible compatibility issues.  Thanks for your feedback, I feel much better now.




Off topic again, what do you guys think about Ubuntu Ultimate Edition?  Has anyone here ever tried it?  The developer certainly makes it sound attractive:
[http://ultimateedition.info/f-a-q/](http://ultimateedition.info/f-a-q/)

Or is it safer for me to just stick to Ubuntu 10.04 at this point, until I become a lot more familiar with this platform?

---

### Post by fly-by-night on 2010-09-14
> **Zenrunner92 said:**
> Off topic again, what do you guys think about Ubuntu Ultimate Edition?  Has anyone here ever tried it?  The developer certainly makes it sound attractive:
[http://ultimateedition.info/f-a-q/](http://ultimateedition.info/f-a-q/)

Or is it safer for me to just stick to Ubuntu 10.04 at this point, until I become a lot more familiar with this platform?

If you have space to spare, make another partition of about 5-10GB and use it for testing/trying-out other systems.  Nowadays I use this method for newer versions of Ubuntu (official), not other systems. When the new version works well I overwrite the old with the next new.

---

### Post by chaanakya_chiraag on 2010-09-14
By the way, just as a reference...you can install the pae (Physical Address Extension) kernel in 32-bit Ubuntu which *will* let your 32-bit installation use all 4 GB of RAM :)

---

### Post by Zenrunner92 on 2010-09-14
> **fly-by-night said:**
> If you have space to spare, make another partition of about 5-10GB and use it for testing/trying-out other systems.  Nowadays I use this method for newer versions of Ubuntu (official), not other systems. When the new version works well I overwrite the old with the next new.

that's a great idea, thanks---with a 500GB HDD I think I can afford a few extra 10GB partitions.   

: )

---

### Post by Zenrunner92 on 2010-09-14
> **chaanakya_chiraag said:**
> By the way, just as a reference...you can install the pae (Physical Address Extension) kernel in 32-bit Ubuntu which *will* let your 32-bit installation use all 4 GB of RAM :)

thanks, I'll definitely do that then!  Yeah, I would feel kind of goofy to not be able to use all of the memory I paid for with the computer...even if it makes no perceptible difference, LOL.

---

### Post by chaanakya_chiraag on 2010-09-16
> **Zenrunner92 said:**
> thanks, I'll definitely do that then!  Yeah, I would feel kind of goofy to not be able to use all of the memory I paid for with the computer...even if it makes no perceptible difference, LOL.
Exactly :D

---

