---
title: "Linux for PSP?(MIPS)"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by milindo on 2011-03-11
Is their a distro/port for linux any distro/ubuntu for the psp, which runs on a MIPS processor??

---

### Post by Matt__ on 2011-03-11
[Yellow Dog]("http://www.yellowdoglinux.com/"), [Debian]("http://www.debian.org/"), [Fedora]("http://fedoraproject.org/"), [Gentoo]("http://www.gentoo.org/"), [OpenSUSE]("http://www.opensuse.org") , and [Ubuntu]("http://ubuntu%20-%20Google%20Search") all run on the PlayStation 3. 

Theres a [ nice guide here]("http://www.tweaktown.com/articles/1305/installing_linux_onto_your_sony_ps3/index.html")

But your chances of success may still very much depend on your firmware version, after 3.15 sony removed the option for "other OS". so good luck. 


//edit there is also [AsbestosOS]("http://www.ps3news.com/PS3-Hacks/video-asbestos-linux-on-ps3-3-41-without-otheros-via-gameos/") if you want to play with programable USB exploits.

---

### Post by milindo on 2011-03-11
> **Matt__ said:**
> [Yellow Dog](http://www.yellowdoglinux.com/), [Debian](http://www.debian.org/), [Fedora](http://fedoraproject.org/), [Gentoo](www.gentoo.org/), [OpenSUSE](www.opensuse.org) , and [Ubuntu](ubuntu - Google Search) all run on the PlayStation 3. 

Theres a [ nice guide here](http://www.tweaktown.com/articles/1305/installing_linux_onto_your_sony_ps3/index.html)

But your chances of success may still very much depend on your firmware version, after 3.15 sony removed the option for "other OS". so good luck. 


//edit there is also [AsbestosOS](http://www.ps3news.com/PS3-Hacks/video-asbestos-linux-on-ps3-3-41-without-otheros-via-gameos/) if you want to play with programable USB exploits.

but really, why? :)
Great reply except for the fact that its about the PS3, not the PSP(the handheld). And because I feel that it will be more useful than the default firmware :P (Also, 333Mhz processor needs more than games)

---

### Post by Matt__ on 2011-03-12
doh!
it was late ok lol...

ok so have you looked here?

> A mipsnommu branch of uClinux 2.4.19 has been ported to the PSP and is available at [http://sites.google.com/site/linuxonpspproject/](http://sites.google.com/site/linuxonpspproject/) uClinux 2.6.22 has recently been ported too and is available at [http://jacksonm88.googlepages.com/linuxonpsp.htm](http://jacksonm88.googlepages.com/linuxonpsp.htm)
And theres an old guide to [install ubuntu 7.10]("http://aruljohn.com/info/pspubuntu/") on psp here

---

### Post by milindo on 2011-03-12
> **Matt__ said:**
> doh!
it was late ok lol...
Any ideas?? (bochs doesn't work for me btw)
*Edit* 
sorry,forgot the link for bochs.. [http://www.hacker.co.il/psp/bochs/](http://www.hacker.co.il/psp/bochs/)

---

### Post by Crimbo on 2011-08-19
There's [psplinux.info]("http://psplinux.info") if you're interested??

---

### Post by me7i on 2011-11-01
there is a french version of ubuntu for psp [http://aruljohn.com/info/pspubuntu/](http://aruljohn.com/info/pspubuntu/) though it is not a true OS as it runs on the psp as a game rather than replacing the firmware, there may be an english version of this but you will have to search it yourself
 [IMG]http://aruljohn.com/info/images/psp/pspubuntu_games.jpg[/IMG]

---

### Post by user26 on 2011-11-25
I'm also interested in this.

My psp stays untouched and dusty since last year... PSP is now a dead commercial machine, but it still can be very usefull.

I'm not a programmer but I joined [http://groups.google.com/group/psp-linux](http://groups.google.com/group/psp-linux). They are trying to improove the uclinux port, but it has no GUI.

I found a cool window manager called xynth, is uses very little RAM

[http://alperakcan.org/?open=projects&project=xynth](http://alperakcan.org/?open=projects&project=xynth)

"Low Memory & CPU Usage; In 1024x768x32bits mode with 253 clients open mem. usage is ~2,5M"

It also can be configured to use 720x480  resolution (TV out) and a usb keyboard could be used.

Somebody compiled a xynth test for psp, But I don't know how this could be added to uclinux.

[IMG]http://dl.dropbox.com/u/757056/frmbuf003.bmp[/IMG]

This is a screenshot from my PSP, it runs really smooth, windows can be resized and grabbed, task bar is working.

There is also a PSPGL library which is like an opengl for psp, I imagine a little icon with those glxgears to test :) LOL. 

But the mips processor is limited because it has no "mmu". 
What does this mean?

I saw a linux working on PS2 with 32 MB RAM... What could be done in the PSP slim with 64 MB?

I wish I knew how to compile things.. I tried to compile xynth but I'm just a noob...

---

