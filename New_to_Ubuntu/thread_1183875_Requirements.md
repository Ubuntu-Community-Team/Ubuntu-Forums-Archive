---
title: "Requirements"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by sheroxe on 2009-06-10
Hi, 
I have an old pc with only 96 MB of ram and running windows xp :S so you can imagine how slow it is.
I want to install ubuntu on it but in ubuntu's homepage says it requieres at least 256mb of ram, is there any way to do it with only 96??

---

### Post by damis648 on 2009-06-10
XP on 96MB ram? :o

You may try xubuntu, which may work by installing with the alternate install CD, but I doubt it. Debian may be able to help, as well as perhaps Puppy Linux. RAM is cheap these days, even 256MB won't hurt.

---

### Post by Het Irv on 2009-06-10
I don't think so, I tried it once with 128mb and it didn't come up far enough for me to even start installing...

---

### Post by sheroxe on 2009-06-10
I thought of something tell me if you think it can work.

What if i take the hard drive out and connect it to my other pc which has enough ram and install ubuntu and then take it back to the old pc

---

### Post by Bigtime_Scrub on 2009-06-10
With 96MB RAM even Debian and Slackware will have problems. 

You should try another distro as even a streamlined Xubuntu will probably not be functional enough for you.

There is Damn Small Linux, TinyMe, or Gentoo maybe.

Puppy will probably not run that well with 96MB RAM...

I'd recommend Damn Small.

---

### Post by Barky on 2009-06-10
> **sheroxe said:**
> I thought of something tell me if you think it can work.

What if i take the hard drive out and connect it to my other pc which has enough ram and install ubuntu and then take it back to the old pc

buy more ram or try another lighter version of linux would be your best bet. Ubuntu would be slow as molasses on 96 mb of ram.

---

### Post by Linux000 on 2009-06-10
I've heard of people installing Ubuntu on i386 systems with 32Mb of ram try this

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by theozzlives on 2009-06-10
That's just not enough for the kernel to load. I tried to run diags on a laptop (233 MHz, 156 MB RAM). I couldn't get Puppy or DSL to load. Never tried Xubuntu.

---

### Post by H2SO_four on 2009-06-10
Sorry I don't have the links, but there are minimal ubuntu/xubuntu installs that have reported ram usage less than 75mb.  There are a couple how-to's in the forum here.

---

### Post by Het Irv on 2009-06-10
> **sheroxe said:**
> I thought of something tell me if you think it can work.

What if i take the hard drive out and connect it to my other pc which has enough ram and install ubuntu and then take it back to the old pc

The danger in that is that the hardware on the computer with more ram may not be compatable, so even if the kernel does boot with that tiny amount of memory... the hardware may not work... Leaving you with nothing more than you started with.

---

### Post by Iusedtowearatie on 2009-06-10
Useful info on this subject in these threads:
[http://ubuntuforums.org/showthread.php?t=1164510](http://ubuntuforums.org/showthread.php?t=1164510)
[http://ubuntuforums.org/showthread.php?t=1159123](http://ubuntuforums.org/showthread.php?t=1159123)

---

### Post by benj1 on 2009-06-10
i would say just try it, i installed ubuntu on a 192mb ram machine it was fine.
i would have thought you could get somewhere with the alternate install cd but gnome would be too heavy, i would suggest debian with a light window manager, or even DSL, it uses an older kernel so will be lighter and more likly to have drivers for hardware, and it can be upgraded to a full debian install, so you should be able a good balance of features and speed.

---

### Post by bodhi.zazen on 2009-06-10
On low ram systems, make a swap partition, and make it 512 + mb

Then boot and install, the system will then use swap for RAM (and it will be slow).

IMO Slackware is best for low RAM systems, as is running without X, as is closing down as many services as possible.

---

### Post by reeseslover531 on 2009-06-10
I have to give my vote for Damn Small Linux, I have installed and had it working beatifully on a laptop with a 500mhz P3 and 64 megs of ram. Give it a try

---

### Post by Linux000 on 2009-06-10
Read previous post, the How-To is here

> **Linux000 said:**
> I've heard of people installing Ubuntu on i386 systems with 32Mb of ram try this

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by sheroxe on 2009-06-10
ok thanks, Ill try to buy more ram but im guessing it wont accept more than 256 mb and it will be hard to find one. The pc is a celeron 1.7 ghz so if i can´t find more ram or its too expensive i think ill just make a big swap and see what happens :S

---

### Post by ______ARMY______ on 2009-06-10
you might try DSL linux i do think that will do it its not ubuntu but it is linux none the less i would try that

---

