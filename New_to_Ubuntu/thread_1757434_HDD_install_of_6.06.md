---
title: "HDD install of 6.06"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by calibra on 2011-05-13
I have only just `moved over` to Linux. Have an old AMD K2-450 and have installed Ubuntu 6.06 ( tried all newer versions but they don`t work) However it doesn`t seem to  have installed onto the HDD everytime I start WITHOUT the cd I get invalid system disk.

Is there a way of installing to HDD so cd not required

Thanks in advance

calibra

---

### Post by oldfred on 2011-05-13
Welcome to the forums.

You do know that the 6.06 desktop is not supported anymore. And the server version expires in June.

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases")
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Does CD boot ok? Have you run install to hard drive. It may not have correctly installed grub legacy to the MBR?

Note that you have grub legacy not grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You may want a newer but a version that supports smaller/older systems. How much memory RAM and hard drive space do you have.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector

---

### Post by QLee on 2011-05-13
oldfred,
This is a minor point but CrunchBang is no longer based on Ubuntu, the newest version is based on Debian Squeeze (stable). It's still a light distro with low RAM requirements and small-footprint apps and thus still worth being included in your list.

---

### Post by calibra on 2011-05-13
> **oldfred said:**
> Welcome to the forums.
 
You do know that the 6.06 desktop is not supported anymore. And the server version expires in June.
 
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases")
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
 
Does CD boot ok? Have you run install to hard drive. It may not have correctly installed grub legacy to the MBR?
 
[COLOR=indigo]*I used option 1 Install.......but requires CD whereby it runs fine !!!!*[/COLOR]
 
Note that you have grub legacy not grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
 
[COLOR=indigo]*Don`t understand `grub legacy I am VERY VERY new to Linux and am only used to MS flavour OS*[/COLOR]
 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
You may want a newer but a version that supports smaller/older systems. How much memory RAM and hard drive space do you have.
 
*[COLOR=indigo]Have 256 MB Ram and 10GB HDD[/COLOR]*
 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)
 
Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
 
[COLOR=indigo]*Will try LUBuntu hopefully this will install ok Only realy need Internet and basic office apps BUT MUST Install to HDD*[/COLOR]
 
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
 
[COLOR=indigo]*Tried XUbuntu and wouldnt let me install*[/COLOR]
 
with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
 
[COLOR=indigo]*Tried LinuxMintand wouldnt let me install*[/COLOR]
 
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector
 
Thanks
 
Calibra
 
PS I managed to get XP pro to install on this PC........but really want Linux

---

### Post by QLee on 2011-05-13
[QUOTE=calibra]...
PS I managed to get XP pro to install on this PC........but really want Linux[/QUOTE]

Wow, I imagine XP runs pretty slow on a K2-450.

I want to add my recommendation to oldfred's, use a more modern release than 6.

With an old system like that you might have better luck installing from the "alternate" CD rather than the live CD. Perhaps try a real full Ubuntu, maybe 10.04 (it's a long term support release). You've described the failures as, wouldn't let me install, but what could prove to be more helpful would be if you quoted the actual error message received, or what the screen looked like or something that would let those of us who aren't looking over your shoulder form some kind of image of what is happening. What gives the most information is when you note the exact command (if you are entering a command) and the exact error message received so we can decide about cause and effect.

Did any of the live CDs you tried get you to a desktop? Did you end up with just a flashing cursor? Did something crash and/or lock up? I'm sure you'll see the point to these examples. You are trying to describe what is happening to someone who is blind to what is happening at your site.

With equipment that old, some or all of the hardware might fail even if you get a distro on there but you could have the opportunity to learn a lot without risking any valuable equipment.

---

### Post by egalvan on 2011-05-13
How much RAM is available? What kind of video?

version 8.04 LTS (Hardy Heron, the previous Long Term) runs well with older (lower resources) systems.

Crunchbang is another good one, as others have stated.
On my work machine (Hardy on a Dell P-4 w/2GB of RAM) I have a rather long list of "low-resource Linux" distros... but I'm on a WinBox right now

But yeah, a K2-450 *is* rather old :)
although lots of RAM will help...
512M is the cat's meow

---

### Post by audiomick on 2011-05-13
> **QLee said:**
> Wow, I imagine XP runs pretty slow on a K2-450...

My last desktop was a K2-400. XP worked fine on it up until I tried to install SP2. Which I removed again pretty much immediately... ;)

---

### Post by wildmanne39 on 2011-05-13
> **oldfred said:**
> Welcome to the forums.

You do know that the 6.06 desktop is not supported anymore. And the server version expires in June.

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases")
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Does CD boot ok? Have you run install to hard drive. It may not have correctly installed grub legacy to the MBR?

Note that you have grub legacy not grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You may want a newer but a version that supports smaller/older systems. How much memory RAM and hard drive space do you have.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html)

Light Linux Distributions - Hardware Testing (RAM)
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Crunchbang: the unofficial Ubuntu Lite
Someone posted this:
Linux Mint XFCE runs fine on a PIII, 500 MHz
8 of the best tiny Linux distros
[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)
Slitaz, DSL, Puppy, Crunchbang, Slackware, Zenwalk, Vector

Hi, these links are a great resource I just wanted to say thank you for posting them.

---

### Post by 3rdalbum on 2011-05-14
6.06 is definitely too old.

If you've got enough RAM, try Ubuntu 11.04 or Ubuntu 10.04 again, and this time post whatever problem stops you from installing it.

If you don't have enough RAM for a recent Ubuntu, then use a recent version of a lighter distribution such as Lubuntu, Puppy Linux, or DSL.

---

### Post by calibra on 2011-05-14
> **QLee said:**
> Wow, I imagine XP runs pretty slow on a K2-450.
 
I want to add my recommendation to oldfred's, use a more modern release than 6.
 
With an old system like that you might have better luck installing from the "alternate" CD rather than the live CD. Perhaps try a real full Ubuntu, maybe 10.04 (it's a long term support release). 
 
[COLOR=indigo]*Q Does the alternate CD mean a FULL install, because I never tried the alternate versions*[/COLOR]
 
You've described the failures as, wouldn't let me install, but what could prove to be more helpful would be if you quoted the actual error message received, or what the screen looked like or something that would let those of us who aren't looking over your shoulder form some kind of image of what is happening. What gives the most information is when you note the exact command (if you are entering a command) and the exact error message received so we can decide about cause and effect.
 
[COLOR=indigo]*I received the eror `Please use a kernel appropoate four your CPU` I have just found the `alternate` downloads page for 10 and 11 will try these both.*[/COLOR]
*[COLOR=#4b0082]If ALTERNATE means full HDD install, then shouldn`t it say so ?[/COLOR]* 
Did any of the live CDs you tried get you to a desktop? Did you end up with just a flashing cursor? Did something crash and/or lock up? I'm sure you'll see the point to these examples. You are trying to describe what is happening to someone who is blind to what is happening at your site.
 
[COLOR=indigo]*The 6.06 did work, only from the CD though couldn`t work out how to use the equivelent of `windows explorer`*[/COLOR] 
 
With equipment that old, some or all of the hardware might fail even if you get a distro on there but you could have the opportunity to learn a lot without risking any valuable equipment.
 
[COLOR=indigo]*Even though I researched quite a bit, feel that the help available is still aimed at someone who already has an understanding of Linux. I don`t like the terminology but need an idiots guide to Ubuntu/Linux I have many many years experience with windows and have built many PC`s, but am Blind to Linux and how it works/what it does*[/COLOR]
 
Thanks for everyones help so far
Calibra
 
[COLOR=indigo]*PS Just tried Xubuntu and Lubuntu and both give me the*[/COLOR] *[COLOR=#4b0082]`Please use a kernel appropoate four your CPU error message.  I hope thatI I have more luck with the alternate 10 and 11 if I my understaning is correct and that they are different versions, although I really think alternate just means a different place to download from.[/COLOR]*

---

### Post by Jagoly on 2011-05-14
> **calibra said:**
> I really think alternate just means a different place to download from.

The alternate install cd is a text based installer instead of a live cd, like the windows XP installer. It's still nice and straightforward. Also, the last thing you want to do is get ubuntu 11.04. Your best bet is with xubuntu 11.04 (what I use) or ubuntu 10.04.

---

### Post by calibra on 2011-05-14
> **Jagoly said:**
> The alternate install cd is a text based installer instead of a live cd, like the windows XP installer. It's still nice and straightforward. Also, the last thing you want to do is get ubuntu 11.04. Your best bet is with xubuntu 11.04 (what I use) or ubuntu 10.04.
 
Tried Alternate 11.04 and got the same kernel/cpu error message xbuntu gives the same error will now try ubuntu 10.04 alternate
 
Thanks
 
Calibra

---

### Post by slooksterpsv on 2011-05-14
11.04 will not work, Lubuntu, Xubuntu, etc. they removed support for anything less than an i686 from the kernel. Yours is I think an i586.

---

### Post by calibra on 2011-05-14
> **slooksterpsv said:**
> 11.04 will not work, Lubuntu, Xubuntu, etc. they removed support for anything less than an i686 from the kernel. Yours is I think an i586.
 
 
Thanks
 
Just installing Ubuntu `Alternate` 10.04.2 and all seems to be working at present.
 
Looking forward to trying it out.
 
Is there a `good` guide to using ubuntu 10.04 for people who are only familiar with windows.
 
Need to `find my way round`
 
 
PS REally think `alternate` should be labelled FULL HDD INSTALL version or similar........

---

### Post by Jagoly on 2011-05-14
> **calibra said:**
> Thanks
 
Just installing Ubuntu `Alternate` 10.04.2 and all seems to be working at present.
 
Looking forward to trying it out.
 
Is there a `good` guide to using ubuntu 10.04 for people who are only familiar with windows.
 
Need to `find my way round`
 
 
PS REally think `alternate` should be labelled FULL HDD INSTALL version or similar........

no no no. the live cd and the alternate cd both install the same thing. The live cd will still install perfectly to (most) HDD's. However, running a live cd (a whole OS from a cd) using a lot more resources than a text based installer.

Glad you got it working :-)
Anything in particular you want to know?

---

### Post by fballem on 2011-05-14
Calibra:

First of all, welccome to Linux. I have been using ubuntu for the past three years. I have been using Microsoft operating systems (DOS and Windows) for more than 25 years. Given a choice, I much prefer ubuntu.

The following is a link to a User Manual for ubuntu 10.04 [http://ubuntu-manual.org/](http://ubuntu-manual.org/) which I hope will prove helpful.

One of the things that I found hardest about learning Linux (and ubuntu) is that it is not Windows. They do things differently here - and the differences are subtle sometimes. People who have minimal computer experience usually have an easier time learning how to use Linux - you and I have had too long to learn the Windows way to do this.

As one of the other posters said, the difference between a normal installation CD and an Alternate CD is that one has a beautiful graphics interface and the other has a text interface. They are both installation CDs. In fact, if you read the description of the Alternate CD from this page [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) you will find that it clearly says that it is an installation CD.

If I may make a final suggestion? I have found that if I approach ubuntu with an open mind, then I will learn. For everything that you can do in Windows, you can do in Linux. It is not Windows, however, so the HOW you do it in Linux may be different than the HOW you would do it in Windows.

If you are in doubt, ask here.

Regards,

---

### Post by calibra on 2011-05-14
Well
 
I tried to install the `alternate` cd of ubunto 10 but halfway through I got error messages about corrupt files, downloaded this via torrent, don`t know if there is anywhere else better to download from.
 
When I tried the `live` version of ubuntu 10 I got the error message about using a kernel appropiate for my CPU.
 
Don`t know why each version behaves differently.
 
So if I finally get the the alternate version 10 to work I suppose it won`t `look` so good as the live cd and presumably install this to HDD from the desktop install icon.
 
Guessing a lot here !!!!!
 
Calibra
 
PS If I finally get the alternate version 10 to install, can I somehow upgrade the desktop to get some or all of the graphic quality of the live cd  version

---

### Post by audiomick on 2011-05-14
> **calibra said:**
> WellPS If I finally get the alternate version 10 to install, can I somehow upgrade the desktop to get some or all of the graphic quality of the live cd  version

I suspect you have not understood something correctly. Once everything is installed, it looks the same as the live CD.  The visual difference is only in the installer. The Alternate CD, as has been mentioned, requires less resources during the install. This is achieved in part by it not having a whizz bang graphical interface like the one on the live CD. Once it as all finished, though, it is the same thing.

---

### Post by calibra on 2011-05-15
> **audiomick said:**
> I suspect you have not understood something correctly. Once everything is installed, it looks the same as the live CD. The visual difference is only in the installer. The Alternate CD, as has been mentioned, requires less resources during the install. This is achieved in part by it not having a whizz bang graphical interface like the one on the live CD. Once it as all finished, though, it is the same thing.
 
 
Thanks audiomick for explaining that. I was definately under a misapprenension !!!
 
I managed to install the `alternate` 10,04 version.....took a few hours though.....
 
Looks good and I am s l o w l y finding my way around.
 
Managed to change the desktop picture, created some folders and downloaded a couple of items.
 
Wondered if the driver updater updates motherboard drivers as well, or do I need to do this manually ???
 
Only other comment is it is a bit slow, especially compared to windows 98 which I had previously.
 
Calibra
 
PS Wondered why if I try to install 10.04 live CD I get the message please use kernel approiate for your CPU BUT the alternate version installs fine ????

---

### Post by audiomick on 2011-05-16
> **calibra said:**
> Thanks audiomick for explaining that. I was definately under a misapprenension !!!
Glad it is clear now. ;)

 > 
Wondered if the driver updater updates motherboard drivers as well, or do I need to do this manually ???
 As far as I know, the only drivers you may have to worry about are proprietary ones for graphics cards, for instance for nVidia graphics. Otherwise, drivers are all part of the kernel, I believe. That is one of the ways that Linux is different to Windows.


> 
Only other comment is it is a bit slow, especially compared to windows 98 which I had previously.Unfair comparison, really. The two systems are a decade apart, and assume completely different levels of hardware development. When W98 came out, an AMD K6 400 was still a fast processor. Of course 98 runs like a rocket on a modern machine, and of course 10.10, which assumes a modern level of hardware, will run slow on a machine that came with 98 on it. 

One of the main differences, though, is that you can leave a sorted Ubuntu install running pretty much indefinitely without a restart, and if you don't mess with it it will keep going pretty much forever. This, and I speak from personal experience, was _*not*_ the case with Windows 98.

> 
 
Calibra
 
PS Wondered why if I try to install 10.04 live CD I get the message please use kernel approiate for your CPU BUT the alternate version installs fine ????
sorry, mate. No idea...

---

### Post by calibra on 2011-05-17
[SIZE=2]Wondered if this question could be answered......bugs me a bit[/SIZE]
 
[SIZE=4][COLOR=purple]*if I try to install 10.04 live CD I get the message please use kernel approiate for your CPU BUT the alternate version installs fine ???? :D*[/COLOR][/SIZE]
*[SIZE=4][COLOR=#800080][/COLOR][/SIZE]* 
*[SIZE=4][COLOR=#800080]Thanks[/COLOR][/SIZE]*
*[SIZE=4][COLOR=#800080]calibra[/COLOR][/SIZE]*

---

### Post by oldfred on 2011-05-17
Did you download the 64bit LiveCd and the 32bit Alternate install disk?

---

### Post by mikechant on 2011-05-17
You said that it's a bit slow (compared to Win98 ) - but you didn't answer the question someone asked earlier - how much RAM does it have?

If you have less than 512Mb it's really worth upgrading. The sort of memory you need (?PC100 maybe) is still readily available and won't cost much. If you've currently got 256Mb it's probably worth getting a 512Mb upgrade if your PC supports it. You should notice a big speed increase in that case.

---

### Post by calibra on 2011-05-17
> **mikechant said:**
> You said that it's a bit slow (compared to Win98 ) - but you didn't answer the question someone asked earlier - how much RAM does it have?
 
If you have less than 512Mb it's really worth upgrading. The sort of memory you need (?PC100 maybe) is still readily available and won't cost much. If you've currently got 256Mb it's probably worth getting a 512Mb upgrade if your PC supports it. You should notice a big speed increase in that case.
 
 
If you read back I actually did state how much RAM I have it`s 256MB
 
and I downloaded the same versions of 10.04 Live and alternate, thats why I didnt understand.....but doesn`t matter because it is installed now.
 
I won`t upgrade this pc any further as it is being given to a friend whom has never used a pc before and wants to see if it is for her.........
 
Thanks 
everyone for all your help
 
Calibra

---

