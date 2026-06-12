---
title: "Ubuntu install with less than 256 MB of RAM"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by unary_01 on 2009-07-10
[SIZE=2]:?:
[/SIZE][FONT=Arial][SIZE=2]I'm new to Ubuntu and want to install it over my current Windows installation. Yet the things is that every time I try to install Ubuntu 9.04 using Wubi, a message pops up saying [/SIZE][/FONT][SIZE=2]"[/SIZE][FONT=Lucida Console][SIZE=2]256 MB are needed. There is currently only 93 MB. Installtion sometimes won't work under these condtions[FONT=Arial]" Or something like that.[FONT=Times New Roman] [FONT=Arial]I was [/FONT][/FONT][/FONT][/SIZE][/FONT][SIZE=2]wondering if I could install it with the following specifications of my PC.

Specifications:

Windows XP Professional SP3
HD: 37.2 GB
S3 Graphics ProSavageDDR
AMD Duron 1200 MHz
95 MB of RAM
[/SIZE]

---

### Post by philcamlin on 2009-07-10
try the alternative cd

---

### Post by Warren Watts on 2009-07-10
RAM is cheap.  Look on Ebay or shop around your local used computer store and add RAM to the PC.

A Duron 1200 has what, a clock doubled 200 MHz Bus Speed?  So all you need is some basic 100MHz RAM.  Maybe $25 at the most for a 256MB stick of RAM....

---

### Post by Jazzy_Jeff on 2009-07-10
First of all if you are trying to install it over you installation of Windows then WUBI will not work. That makes it so you can install Ubuntu to run inside of windows. You need to burn the Ubuntu image to disk and reboot the system.

I would not try installing Ubuntu without more ram. You can try other light weight linux distributions like Puppy Linux or Damn Small Linux.

---

### Post by QIII on 2009-07-10
Actually, if the motherboard is configured for 168 pin RAM, it can be very expensive.

Older notebooks can be expensive to upgrade as well.

EDIT:  And be aware that ECC will most likely NOT work on anything but a server ... so don't be attracted by the cheaper price.

---

### Post by Ji Ruo on 2009-07-10
> **unary_01 said:**
> 
Specifications:

Windows XP Professional SP3
HD: 37.2 GB
S3 Graphics ProSavageDDR
AMD Duron 1200 MHz
95 MB of RAM
[/SIZE]

I'm amazed that you got XP to work with 95MB of ram. I seriously doubt you will get ubuntu to install with wubi. You want to restart the computer with the CD inside, and with booting from the CD enabled in your BIOS settings (look for the key to press when your computer first boots up). Even then I don't think you will be able to install and it will hang up during the install (you can try though). If you can't get it to work your options are upgrade the memory or try a low spec linux distro like slitaz or DSL, which will work fine with that amount of memory.

---

### Post by ahndoruuu on 2009-07-10
yeah...uhh...

all I can advise is to try to get more RAM. you'll need it eventually for something or other, plus your computer experience would be that much smoother.  I have 3GB RAM and it runs smooooth no matter how many applications and windows I open.

---

### Post by hyperdude111 on 2009-07-10
95 mb of RAM ? How does xp work. You need more RAM before considering this.

---

### Post by bela42 on 2009-07-10
A while ago I did install 9.04 on an old notebook with only 256 MB. I had to use the alternate CD, but GNOME was a no go. Xubuntu did install and finally boot in hours, but was not usable. So I installed and switched to LXDE, now I do at least boot into a desktop.
But, what then? Forget running Firefox. Midori runs, but too unstable, didn't try Opera yet. And that was 256 MB...
So if you plan to actually use that machine in contrast to me just playing around you will need more RAM.

And you can actually use XP on that?

---

### Post by earthpigg on 2009-07-10
wow, i didn't realise xp's requirements where so low:

[http://www.microsoft.com/windowsxp/sysreqs/pro.mspx](http://www.microsoft.com/windowsxp/sysreqs/pro.mspx)

```

PC with 300 megahertz or higher processor clock speed recommended; 233 MHz minimum required (single or dual processor system);* Intel Pentium/Celeron family, or AMD K6/Athlon/Duron family, or compatible processor recommended

128 megabytes (MB) of RAM or higher recommended (64 MB minimum supported; may limit performance and some features)

1.5 gigabytes (GB) of available hard disk space*
```

unary_01:

as others have pointed out, ubuntu does indeed require 256 mb of ram.


plenty of other distros, however, have much more modest requirements:

*puppy linux
*dsl
*arch (1 reached)

---

### Post by renbla on 2009-07-10
> **unary_01 said:**
> [SIZE=2]:?:
[/SIZE][SIZE=2]Windows XP Professional SP3
HD: 37.2 GB
S3 Graphics ProSavageDDR
AMD Duron 1200 MHz
95 MB of RAM
[/SIZE]

Is this some kinds of joke??? you've gotta be kidding me. Maybe i'm too young to know a less-then-128mb RAM could exist these days so pardon me ^^. You should buy more RAM stick. Even a poor country like mine, ppl that have have 1gb of RAM like feel sad :p

---

### Post by mikodo on 2009-07-10
> **Jazzy_Jeff said:**
> First of all if you are trying to install it over you installation of Windows then WUBI will not work. That makes it so you can install Ubuntu to run inside of windows. You need to burn the Ubuntu image to disk and reboot the system.

I would not try installing Ubuntu without more ram. You can try other light weight linux distributions like Puppy Linux or Damn Small Linux.


Or, following the advice from another thread I initiated, you might consider Debian 5.1 another distro of GNU/Linux, which uses very little resources installed.

---

### Post by Cato2 on 2009-07-10
I really recommend you try Crunchbang - it's very lightweight and works in less than 128 MB, *yet it's also Ubuntu based*, so much of what you learn in Crunchbang applies to Ubuntu and vice versa.  It uses OpenBox which is a lighter alternative to Ubuntu's default GNOME desktop environment.  

There's a friendly forum community, and you can also ask questions on the Ubuntu forums as long as you say it's Crunchbang.  It is derived from Ubuntu Jaunty 9.04 (latest version) so as long as your hardware works OK with this version, you are using an up to date system and get all the Ubuntu security updates etc.

See [http://crunchbanglinux.org/](http://crunchbanglinux.org/) - it comes with Firefox, Skype, Pidgin (for MSN/Yahoo/AOL instant messaging), etc.  It also has Flash enabled, an iTunes equivalent (Rhythmbox), etc.  All this will save you a LOT of time particularly on an older machine where installing software is more time consuming anyway.  See [http://crunchbanglinux.org/wiki/screenshots](http://crunchbanglinux.org/wiki/screenshots) for some screenshots of the various apps.  You may need to try Crunchbang Lite given the 93 MB RAM - see [http://crunchbanglinux.org/wiki/downloads](http://crunchbanglinux.org/wiki/downloads) - it has some lighter apps to save RAM.

If you don't like the dark look of Crunchbang, this is quite easy to change, ask on the Crunchbang forums.

I have also used Puppy (very easy to get going) and Damn Small Linux, but they are very different to Ubuntu.  Another very light alternative is SliTaz - includes very little out of the box though.  I would only try those if Crunchbang isn't right for you, and start with Puppy. Most of these systems do NOT have such good hardware support for newer gizmos as Ubuntu, but they are fine on older systems usually.  Also they don't provide security updates.

Debian might be an option if you already know quite a bit of Linux, but Crunchbang is where I would start.

For more threads on Crunchbang and some discussion of other lightweight Linuxes, see [http://ubuntuforums.org/tags.php?tag=crunchbang](http://ubuntuforums.org/tags.php?tag=crunchbang)

---

### Post by Bobber47 on 2009-07-10
I concur with the suggestions to choose another distro.  I have an old 128 MB laptop that worked with older versions of Xubuntu (7.04), but encountered problems after upgrading.

DSL: good but quite limited repositories
Puppy: fast, more extensive repos., small versions available
Vector: slackware based, good with older hardware
Debian: great, but work to get setup
Knoppix: great live system, good hardware config., only KDE that actually 
          would run (barely) on the above laptop
TinyCore: extremely small, add what you need, but you'll need a lot
Zenwalk, TinyMe ......

Haven't tried Crunchbang - sounds interesting....

---

### Post by egalvan on 2009-07-10
[COLOR="Red"]TinyCore Linux[/COLOR]

[I]What are the minimum requirements?

An absolute minimum of RAM is 32mb. TC won't boot with anything less, no matter how many terabytes of swap you have.
The minimum cpu is i486DX (486 with a math processor).

[B]A recommended configuration:
Pentium 2 or better, 128mb of ram + some swap [/B][/I]

--------------------------

I cannot find requirements on the[COLOR="Red"] Puppy Linux[/COLOR] web-site.
I have used it with as little as 128M RAM; it ran well.

I have no recent experience with [COLOR="Red"]DamSmallLinux[/COLOR]
(almost two years since last used)

---

### Post by mikodo on 2009-07-10
comment: This becoming a great thread. I hope it can continue

---

### Post by credobyte on 2009-07-10
> **egalvan said:**
> 
I cannot find requirements on the[COLOR=Red] Puppy Linux[/COLOR] web-site.


This article might be interesting for some of you ( Puppy Linux related ) : [http://linux.com/archive/articles/56429](http://linux.com/archive/articles/56429)

---

### Post by egalvan on 2009-07-10
> **credobyte said:**
> This article might be interesting for some of you ( Puppy Linux related ) : [http://linux.com/archive/articles/56429](http://linux.com/archive/articles/56429)

Wow, I think this is the exact same article that led me to try Puppy!

I had been struggling with DSL, and not having any luck.

Puppy was an eye-opener!

Small download, easy to boot, easy to run.
And easy to install to a hard drive, it turns out!
I triple-boot XP, Puppy and Ubuntu on almost all my Linux machines.

The only draw-back to the article is that it's out of date...

It's two years old, and Puppy have gone though some major revisions, and the memory requirement have gone up.

The good thing is that all the older versions of Puppy are still available, so testing with these smaller versions is quite easy.

As for me, I installed it on a 933MHz P-III, 256M RAM Dell Optiplex GX-110.
4M shared video RAM. Onboard sound and NIC. USB and FireWire card.
All found "out-of-box".
It ran extremely well. Fast and totally stable.
Unfortunately, the client did not like it and demanded XP be installed instead.
Then he complained about how slow the computer and become.
Basically accused me of swapping out a much older/slower computer.
So I popped in the Puppy LiveCD, and showed him the error of his ways. :)

And just for grins, I also installed it on my AMD Quad-Core, 8GB RAM Heavy Metal.
Again, fast :) and totally stable.
Played music, found the camera, memory card reader, Gigabit NIC, etc.
Amazing piece of software.

---

### Post by random turnip on 2009-07-10
In theory is should work, but i would advise trying Xubuntu, it's designed more for that type of spec and will run pretty fast on it.


Actually, either get some more RAM or try and run DeLi Linux, even Xubuntu won't run on that.
There is no shame in having an old computer, i have one sitting around with a 10GB HDD (which was considered to be massive at the time), i don't even know if it HAS RAM, lol.

---

### Post by snowpine on 2009-07-10
> **unary_01 said:**
> 
Windows XP Professional SP3
HD: 37.2 GB
S3 Graphics ProSavageDDR
AMD Duron 1200 MHz
95 MB of RAM


I would recommend sticking with Windows on those specs, if it works okay for your needs. I would not personally install a modern Linux OS with anything less than 256mb of ram. Certainly anything in the Ubuntu family (including Xubuntu, Crunchbang, etc.) is out of the question with only 95mb. Perhaps a very tiny distro such as DSL might work?

---

### Post by Cato2 on 2009-07-10
> **snowpine said:**
> ...  Certainly anything in the Ubuntu family (including Xubuntu, Crunchbang, etc.) is out of the question with only 95mb. 

I don't agree - Xubuntu is too heavy for 96MB but I see no reason why Crunchbang Lite will not work (possibly after disabling a few background apps such as Conky).

[U-Lite]("http://u-lite.org/") (formerly Ubuntulite) aims at 56MB RAM (without needing swap) - so if for some reason Crunchbang is too heavy that would be a good place to start, assuming Ubuntu is preferred.

Puppy or similar would be easier to get started with than U-Lite.

---

### Post by halitech on 2009-07-10
I've never tried this with less then 128 meg of ram but it might work if you go with LXDE instead of XFCE

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by snowpine on 2009-07-10
> **Cato2 said:**
> I don't agree - Xubuntu is too heavy for 96MB but I see no reason why Crunchbang Lite will not work (possibly after disabling a few background apps such as Conky).

Have you personally tried Crunchbang Lite with 96mb?? I have tested it on my old 128mb laptop, and it is dog slow once you have a few browser windows open. Like all Ubuntu variants, it really needs 256mb to "blossom" in my opinion.

---

### Post by Cato2 on 2009-07-10
> **snowpine said:**
> Have you personally tried Crunchbang Lite with 96mb?? I have tested it on my old 128mb laptop, and it is dog slow once you have a few browser windows open. Like all Ubuntu variants, it really needs 256mb to "blossom" in my opinion.

The speed really depends on the browser - multi-tab browsing is always going to be a big challenge on any computer with only 96MB.  I do have a 96 MB laptop that I've used with DSL and Puppy, before Crunchbang came along, and found that using Firefox or SeaMonkey was pretty slow.  Opera was quite fast and I hear that Midori or Kazehakaze (sp?), included in Crunchbang Lite, is pretty good.  

Someone else's experience is that [128 MB is enough for Crunchbang]("http://crunchbanglinux.org/forums/post/1176/#p1176"), though they don't say if they used it for Web access.  There's also a report of [installing in 96MB using the alternative installer]("http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation#post-775") (maybe that was you though as it's the same username :) )

Since I really like Ubuntu for its available software and security updates, I'm prepared to do some slimming-down work to get it to fit in 96 MB, but I think Crunchbang is a good place to start and it wouldn't be too hard.  I have VMs with U-Lite and Crunchbang, I just need to try them on this laptop when I get some spare time.

One final pointer for those with good Linux skills: try [compcache]("http://lwn.net/Articles/334649/"), a set of kernel modules that effectively increases your available RAM - what it does is use some of your RAM as a swap disk that's heavily compressed.  Since swapping to/from this compressed-RAM drive is much faster than swapping to disk, it's almost as good as having (say) that amount of RAM multiplied by the compression ratio.  Worth a try at any rate - and one reason to use Ubuntu as a base is that it's really easy to just type "aptitude install build-essential" etc to get the tools you need to recompile the kernel.

---

### Post by LewRockwell on 2009-07-10
> **snowpine said:**
> Have you personally tried Crunchbang Lite with 96mb?? I have tested it on my old 128mb laptop, and it is dog slow once you have a few browser windows open. Like all Ubuntu variants, it really needs 256mb to "blossom" in my opinion.

"dog slow" is putting it NICELY...

.

---

### Post by QIII on 2009-07-10
> **renbla said:**
> Is this some kinds of joke??? you've gotta be kidding me. Maybe i'm too young to know a less-then-128mb RAM could exist these days so pardon me ^^. 

Jeez.

I remember how excited I was to get 4k...

---

### Post by Warren Watts on 2009-07-11
> **QIII said:**
> I remember how excited I was to get 4k...

I remember back in the early 1990's I had a 25 Mhz 386 SX Packard Bell PC I purchased new (And the LAST computer I ever bought off the shelf!) that came with Windows 3.0 and 2MB or RAM.  I was so excited when I bought an additional 2MB and boosted it to 4MB!

Oh, the difference in performance doubling the available memory made!  LOL

---

### Post by tiga2001 on 2009-07-11
Yeah, I would say the same thing as others in terms of upgrading the ram. I mean, in the end, it's still cheaper than buying a whole new computer. But at your computer's configuration, it might be better to upgrade the entire motherboard.

Also, I tried out lxde on ubuntu, and it feels a lot faster than xfce on ubuntu. I can't say how it compares to crunchbang, though, because I didn't try that. I love firefox, but with this amount of memory, I, too, think firefox is out of the question. Perhaps if you install flashblock it will run fast.

---

