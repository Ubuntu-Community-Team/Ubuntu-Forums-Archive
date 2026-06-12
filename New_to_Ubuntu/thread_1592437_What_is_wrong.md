---
title: "What is wrong?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by krikett on 2010-10-10
jens@svettlana:~/rtl-wifi$ sudo make
[sudo] password for jens: 
make -C /lib/modules/2.6.35-22-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2
jens@svettlana:~/rtl-wifi$

---

### Post by mörgæs on 2010-10-10
I don't know, but a better title will help you get an answer.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Rubi1200 on 2010-10-10
> **mörgæs said:**
> I don't know, but a better title will help you get an answer.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
+1

Also, please tell us things like which version of Ubuntu you are using, what you are trying to do and why, as well as any other information you think might be relevant.

Have you checked this?
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

Thanks.

---

### Post by krikett on 2010-10-10
ubuntu 10.10 maverick.
Trying to install [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing). And when i try make that is what i got.

---

### Post by themusicalduck on 2010-10-10
According to that wiki page the drivers you are trying to compile are included in kernels since 2.6.25 and your terminal output says you have 2.6.35. So you should already have them without needing to compile and install.

Why are you trying to compile and reinstall the drivers? Is there a particular problem you're having?

---

### Post by krikett on 2010-10-10
[COLOR=#000000]That was very embarrassing. [/COLOR]A friend said I had to install the driver. But if i have it then ok. But do i need to [COLOR=#000000]disable the [/COLOR][COLOR=#000000]embedded device? If so  how? 
[/COLOR]

---

### Post by themusicalduck on 2010-10-10
It's an easy mistake to make. Most people assume that Linux works in the same way as Windows, in that every driver needs to be installed separately, but in most cases you don't need to install anything.

You need to tell us what it is you're trying to do. By embedded device do you mean wireless device? Why do you want to disable it? It can probably be disabled, but I think it would take a bit of command line usage and researching to find out exactly what module it uses so you could blacklist it.

If you're trying to get your wireless to work, then do you know what wireless device you have? Also, I think it's unlikely since the wiki said they should be installed by default, but it is worth checking System > Administration > Hardware Drivers to see if a driver can be activated from there.

Otherwise, to find out what wireless card you have, you could open a terminal (Applications > Accessories > Terminal), type in lspci and hit enter, then post the output on here.

---

### Post by krikett on 2010-10-10
i try to install alfa-awus036h because my [COLOR=#000000]integrated wlan card is not so good. if that you saying is right, i don't need to install the alfa awus036h driver, [/COLOR]but I guess I have to disable the integrated. So [COLOR=#000000]what do I do?

[/COLOR]sorry for all the questions. But I have used windows for 12 years, so it takes some time to understand something new.

---

