---
title: "flash player crash on fullscreen"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Darthpc on 2010-09-02
I have Ubuntu 10.04 but it did this on previous version as well. The Firefox flash player plugin crashes when you go to fullscreen. I have the latest version of the plugin installed I tested it against a Windows installation and it seems to be isolated to the Linux version of firefox any help resolving this is greatly appreciated

---

### Post by QIII on 2010-09-02
I don't think it is the Linux version of Firefox, but of Flash.  The Linux version of Flash has always been, well, crap.  (Adobe -- Are you listening?)

You might take a look at lovinglinux blog and help here:

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

Or his compendium of Firefox optimizations here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Kellemora on 2010-09-02
Forget about Flash-Aid from LovingLinux

I installed it, it appeared to be working OK.

However, the thrill was short lived when I now find myself faced with the problem of I can move between screens anymore, all I get is a GRAY screen the first attempt and a WHITE screen the second attempt.

Disabling Flash-Aid did not help.
Uninstalling it leaves you with NO version of Flash, and I can't find a way of getting a 64 bit version to reinstall it in my computer.

In other words, since trying Flash-Aid, I'm virtually SOL as far as using this computer for much of anything anymore.......

I've already lost 6 hours trying to undo the MESS Flash-Aid has caused!

TTUL
Gary

---

### Post by NoNameWill on 2010-09-02
I am running 64 bit 10.4 and the only thing that got flash working some what right is flash-aid. 

Before I installed flash-aid I got a lot of gray screens and could not play you-tube videos that were embedded in html other than on youtubes site.

For me flash-aid works better than anything else.

---

### Post by QIII on 2010-09-02
> **Kellemora said:**
> Forget about Flash-Aid from LovingLinux

I installed it, it appeared to be working OK.

However, the thrill was short lived when I now find myself faced with the problem of I can move between screens anymore, all I get is a GRAY screen the first attempt and a WHITE screen the second attempt.

Disabling Flash-Aid did not help.
Uninstalling it leaves you with NO version of Flash, and I can't find a way of getting a 64 bit version to reinstall it in my computer.

In other words, since trying Flash-Aid, I'm virtually SOL as far as using this computer for much of anything anymore.......

I've already lost 6 hours trying to undo the MESS Flash-Aid has caused!

TTUL
Gary

Flash-Aid has been a god-send for many, but everyone's mileage varies.

Adobe's support for the 64-bit Linux version of Flash has been pulled due to some massive security holes, and it doesn't look like they plan to do anything with it any time soon.

I dumped it and installed the flash installer from Synaptic.  Sure, it's 32 bit with a wrapper.  But since Flash for Linux was always crap, I'm no worse off.

---

### Post by Jammerton on 2010-09-02
this may or may not help. But I use konquerer instead of firefox (I'm running kubuntu) and it handles flash WAY better.

---

### Post by lovinglinux on 2010-09-02
> **Kellemora said:**
> Forget about Flash-Aid from LovingLinux

I installed it, it appeared to be working OK.

However, the thrill was short lived when I now find myself faced with the problem of I can move between screens anymore, all I get is a GRAY screen the first attempt and a WHITE screen the second attempt.

Disabling Flash-Aid did not help.
Uninstalling it leaves you with NO version of Flash, and I can't find a way of getting a 64 bit version to reinstall it in my computer.

In other words, since trying Flash-Aid, I'm virtually SOL as far as using this computer for much of anything anymore.......

I've already lost 6 hours trying to undo the MESS Flash-Aid has caused!

TTUL
Gary

I have already solved Kellemora's problems described in the post above by helping him directly through e-mail. The problems have nothing to do with FLASH-AID and can be fixed with the solutions from [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

There is an additional problem tho. Ubuntu 8.04 Hardy Heron repositories does not offer flash 10. It says it is flash 10 in Synaptic, but in fact is 9.0.280. This version is not compatible with some sites like Facebook.

> **NoNameWill said:**
> I am running 64 bit 10.4 and the only thing that got flash working some what right is flash-aid. 

Before I installed flash-aid I got a lot of gray screens and could not play you-tube videos that were embedded in html other than on youtubes site.

For me flash-aid works better than anything else.

:guitar:

> **QIII said:**
> Flash-Aid has been a god-send for many, but everyone's mileage varies.

:popcorn:

Most problems occur on systems running Ubuntu 8.04, specially 64bit, because of the available flash version.

---

### Post by aoia456kl24 on 2010-11-01
My flash player was crashing on attempts to go full screen - some searching on the web suggested preloading the libGL library BUT it is not in the place you would expect on Ubuntu: 
most pages said to <code>export LD_PRELOAD=/usr/lib/libGL.so.1</code>
but in Ubuntu (10.10, 32 bit) the library is in <code>/usr/lib/mesa/libGL.so.1</code>
when I run firefox with this mesa library preloaded, it all works fine!

John

---

