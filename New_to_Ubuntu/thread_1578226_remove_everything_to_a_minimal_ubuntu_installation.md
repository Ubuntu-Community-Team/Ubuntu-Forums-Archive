---
title: "remove everything to a minimal ubuntu installation"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by psorincatalin on 2010-09-20
hey there

i have xubuntu 10.04.1 installed with wubi, but my computer is still slow. i am a newbie regarding to linux (i only have 3 months of playing with the *buntus) so i want to do the following:

1. stripping down xubuntu to ubuntu minimal (but i don't know how to do that, hopefully i'll get some responses on how to do it) 

2. from the cli i want to do the following:
     a) sudo  apt-get install xorg xterm wdm icewm menu firefox --no-install-recommends
     b) sudo service wdm start

did i get the commands right ?
will this be enough to get a basic GUI working ?

thanks!

---

### Post by brujoquizz on 2010-09-20
Maybe it would be easier (and better for windows) to remove ubuntu from inside your Windows operative system, make a partition (with gparted, that comes in ubuntu, should be easier) and install a debian minimal, which is almost an ubuntu without all the desktop things. And from that minimal installation start installing the things you want.

---

### Post by rockerphil on 2010-09-20
when i first started using Linux it was with Fluxbuntu, a now dead *buntu distro and it was running on an old Dell Dimension L500cx running a 500 MHz Intel Celeron processor with 128 mb of pc100 SDRAM. well once Fluxbuntu died i was in the same boat you're now in. i wanted a distro that would run well on the modest specs my machine had but i wasn't yet experienced enough to install Slackware of Debian and i wanted to stick with the Ubuntu base. this tutorial helped a lot, and i hope it'll help you.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

hope this helps,

Phil

---

### Post by psorincatalin on 2010-09-20
if i do a minimal debian install, will i be able to use ubuntu repositories, and if so, how do i add them ?

will i have problems wile booting into windows again because of grub overriding the windows boot manager ?

---

### Post by kaldor on 2010-09-20
Wubi is a bad way of using Ubuntu. It's dead slow and glitchy from my experiences.

---

### Post by cavh on 2010-09-20
I'v used this method and recommend it:

[http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/]("http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/")

---

### Post by warfacegod on 2010-09-20
Indeed. Wubi was never intended for more than temporary use as an alternative way to test Ubuntu.

As far as reducing a full install down to minimal goes I've tried this myself a few times. It is a *huge* amount of work, never seemed to be as effective as an actual minimal install, and left my system buggy as hell. I would suggest starting with a minimal and building from there. If that's not your thing then there are lightweight distros that might serve you better. CrunchBang's stable version is based on Ubuntu 9.04, for example.

---

### Post by psorincatalin on 2010-09-20
> **rockerphil said:**
> when i first started using Linux it was with Fluxbuntu, a now dead *buntu distro and it was running on an old Dell Dimension L500cx running a 500 MHz Intel Celeron processor with 128 mb of pc100 SDRAM. well once Fluxbuntu died i was in the same boat you're now in. i wanted a distro that would run well on the modest specs my machine had but i wasn't yet experienced enough to install Slackware of Debian and i wanted to stick with the Ubuntu base. this tutorial helped a lot, and i hope it'll help you.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

hope this helps,

Phil




okay, i've given up stripping down xubuntu and i want to do a linux partition with gparted on which i want to install ubuntu minimal + the commands listed above. is there any risk in doing this ?
is grub going to override windows boot manager? (other tips/hints?)
i also want to ask you what is the best .deb distro for my pc (500 mhz cpu, 64 mb ram)
i heard that gentoo has an extra andvantege in speed due to porting (what is that, and does it read .deb files?)

---

### Post by lobralleo on 2010-09-20
As far as I can remember, Gentoo is not .deb based, instead it builds every single package from sources. This of course means a faster response since the OS is tailored on the machine, however it could be very slow when installing stuff.

I am wondering if with such a lightweight PC you would fare better with something like Puppy Linux; you can browse DistroWatch for a list of light and active Linux distros:

[http://distrowatch.com/search.php](http://distrowatch.com/search.php)

---

### Post by snowpine on 2010-09-20
> **psorincatalin said:**
> i also want to ask you what is the best .deb distro for my pc (500 mhz cpu, 64 mb ram)

You need more RAM, period. :(

Please read the [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").

64mb is not even enough for a command-line only (no GUI) install.

---

### Post by warfacegod on 2010-09-20
I bet that thing would run a Live SliTaz okay.

---

### Post by psorincatalin on 2010-09-20
does puppy linux read .deb files ?

i heared of tinycore linux, a linux distro that has the lowest system req., works even on old computers such as mine
i also heared of crunchbang linux, this one has an advantage of reading .deb binaries

can someone tell me which one is more resource friendly ?

oh and btw i like to have a start menu-like feature, it's a must, so is this possible in tinycore/crunchbang ?

---

### Post by Dustin2128 on 2010-09-20
> **brujoquizz said:**
> Maybe it would be easier (and better for windows) to remove ubuntu from inside your Windows operative system, make a partition (with gparted, that comes in ubuntu, should be easier) and install a debian minimal, which is almost an ubuntu without all the desktop things. And from that minimal installation start installing the things you want.
indeed, this helps quite a lot. Its my understanding that when it runs in windows, it runs on a non-native FS (NTFS) which slows it down significantly. Also, though fluxbuntu is now defunct, openbox and fluxbox both still make excellent and light desktop environments.

I do not believe that puppy reads .debs. 
Also, SliTaz is quite excellent on older hardware. It gave life to my old P2 machine with 128MB RAM. In retrospect though, maybe I should've let it die...

---

### Post by perspectoff on 2010-09-20
The new version (5 or greater) of Puppy Linux now uses Debian (actually Ubuntu minimal server) and .deb files, yes. Xubuntu is a memory hog and uses Gnome. It is no longer useful for hardware-handicapped computers.

But you aren't going to be able to use much of anything with less than 128 Mb RAM, except for DSL (Damn Small Linux).

DSL is not pretty. I don't think it is consistently maintained anymore. But it sure is fast and runs in the tiniest of environments.

You can't run Windows with 64 Mb. Minimum is 512 Mb (even for XP). If you are talking about Wubi that implies you have Windows on your machine, which means you must have at least 512 Mb RAM. So I am assuming you are therefore talking about a virtual machine using 64 Mb, or something like that, with the intention of allowing Windows to limp along with (512 Mb - 64 Mb =) 448 Mb RAM in the background.

If that is the case and your computer has about 512 Mb total, why not create a new partition and then install Ubuntu to the new partition? Then you could use all your memory for Ubuntu and not worry about Windows while Ubuntu is running. With 512 Mb dedicated to it, you could run a regular Ubuntu installation and not worry about "light" installations like Puppy, Lubuntu, Xubuntu, or others.

Wubi is a waste of time unless you have lots and lots of RAM to start with.

---

### Post by warfacegod on 2010-09-20
I've run XP on 256 MB RAM with no problems.

---

### Post by snowpine on 2010-09-20
64mb is not enough RAM for an enjoyable modern (Facebook, Youtube, etc.) Linux experience.

[Puppy Linux hardware requirements]("http://www.puppylinux.org/wikka/MinReq"):

>     *  CPU : Pentium 166MMX
    * RAM : 128 MB physical RAM for releases since version 1.0.2 or failing that a Linux swap file and/or swap partition is required for all included applications to run; 64 MB for releases previous to 1.0.2
    * Hard Drive : Optional
    * CDROM : 20x and up

[SliTaz system requirements]("http://www.slitaz.org/en/doc/releases/3.0/relnotes.en.html"):

> SliTaz GNU/Linux supports all machines based on the i486 or x86 Intel compatible processors. A minimum 192MB of memory is recommended to use the core LiveCD. 80MB is needed for the "slitaz-loram" flavor and 16MB for the "slitaz-loram-cdrom" flavor.

With the slitaz-loram flavor, the system is less responsive, but allows you to graphically install SliTaz on very old machines with limited resources. Once installed, SliTaz works well with a minimum of 16MB memory, but forget about using Firefox to surf the web - you'll have to use the text based 'links' for example. 

---

### Post by lbrty on 2010-09-20
> **psorincatalin said:**
> 
i also want to ask you what is the best .deb distro for my pc (500 mhz cpu, 64 mb ram)
i heard that gentoo has an extra andvantege in speed due to porting (what is that, and does it read .deb files?)

Since you want an OS based on .deb, then I would suggest purchasing a stick of RAM (the max that your mobo can take) for $10 on eBay.

---

### Post by cascade9 on 2010-09-21
> **snowpine said:**
> You need more RAM, period. :(

Please read the [Ubuntu System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").

64mb is not even enough for a command-line only (no GUI) install.

+1. You could probably boost your RAM up to at least 512MB (depending on your chipset). 

> **perspectoff said:**
> The new version (5 or greater) of Puppy Linux now uses Debian (actually Ubuntu minimal server) and .deb files, yes. Xubuntu is a memory hog and uses Gnome. It is no longer useful for hardware-handicapped computers.

You can't run Windows with 64 Mb. Minimum is 512 Mb (even for XP). If you are talking about Wubi that implies you have Windows on your machine, which means you must have at least 512 Mb RAM. So I am assuming you are therefore talking about a virtual machine using 64 Mb, or something like that, with the intention of allowing Windows to limp along with (512 Mb - 64 Mb =) 448 Mb RAM in the background.


Errr......

Xubuntu does NOT use gnome. It uses Xfce. Xfce is actually pretty light, its just the extra stuff that they put into xubuntu that made it slower, and more of a memory hog than lots of other Xfce distros. 

LMAO @ "Minimum is 512 Mb (even for XP)". Not even close. 64MB is the minimum requirement for XP- 

> The minimum hardware requirements for Windows XP Professional include: 
[LIST]
[*]Pentium 233-megahertz (MHz) processor or faster (300 MHz is recommended)
[*]At least 64 megabytes (MB) of RAM (128 MB is recommended)
[/LIST]


[http://support.microsoft.com/kb/314865](http://support.microsoft.com/kb/314865)

XP on 64MB is a fast way to get to 'drive flog land', it wont stop swapping...ever. (that is 'stock', there are things you can do to help that) Painful. 128MB is fine, untill you go to open anything that takes any more power than solitare. Once you get to 256MB+, XP runs quite happily. 

I dont know where people get the whole "XP needs 512MB to run" idea, its totally false.

---

### Post by warfacegod on 2010-09-21
I've had SliTaz Live running very nicely on an old IBM Thinkpad with a P II @ 233 MHz and 128 MB RAM. I can only assume it would do *okay* with 64 MB RAM.

And, as I said before, my XP ran fine on 256 MB RAM. The only thing that really gave it fits was the fractal generator I was trying.

---

### Post by mastablasta on 2010-09-21
> **cascade9 said:**
> +
I dont know where people get the whole "XP needs 512MB to run" idea, its totally false.
 
 
it runs on 256 Mb but VERY slow. especially after SP are installed (SP1 is actually quite fast on it). Oh and dont' forget you need antivirus and firewall. I had it on 256 and took about 10-16 minutes to boot. now i have ubuntu and it boots in 1 minute.
 
also i think after SP 2 they raised minimum requirements to 256 MB ram, and recomended to 512 MB. could be wrong though. 
 
@psorincatalin
 
What good is it if it runs .deb files and uses Ubuntu repositories if it can't run the programmes in it?
 
You need more ram or try one of distros that are light but don't use debian or ubuntu  repositories. such as slitaz and now sort of dead DSL.

---

### Post by cascade9 on 2010-09-21
> **mastablasta said:**
> it runs on 256 Mb but VERY slow. especially after SP are installed (SP1 is actually quite fast on it). Oh and dont' forget you need antivirus and firewall. I had it on 256 and took about 10-16 minutes to boot. now i have ubuntu and it boots in 1 minute.
 
also i think after SP 2 they raised minimum requirements to 256 MB ram, and recomended to 512 MB. could be wrong though. 
 

I've had WinXP SP3 with 128MB of RAM boot faster than that. Its possible that you had bitrot, windows errors, or something lof that order. 

I've had no issue with XP SP2 or 3 on 256MB machines.  As far as I know, microsoft didnt change the CPU/RAM requirements at all either (they did change the HDD reqirements). 

> **warfacegod said:**
> I've had SliTaz Live running very nicely on an old IBM Thinkpad with a P II @ 233 MHz and 128 MB RAM. I can only assume it would do *okay* with 64 MB RAM.

And, as I said before, my XP ran fine on 256 MB RAM. The only thing that really gave it fits was the fractal generator I was trying.

I'm pretty sure that Siltaz should run on 64MB, but it would be much happier with 128MB+. 

Fractals, LOL. There is a great reason to have 4GB+ of RAM. ;)

---

### Post by psorincatalin on 2010-09-21
i'm using a super slim version of xp sp2, about 16 processes at startup, uses alot less memory than normal xp sp3. i went for xubuntu hoping that my pc would perofrm better

i guess i'll go fow ubuntu minimal + wdm display manager + tinywm window manager

or should i go with debian minimal + wdm display manager + tinywm window manager ?

i would appreciate if you could tell me a slimmer display manager, other than wdm

---

### Post by kelvin spratt on 2010-09-21
Mepis do a version called Antix it runs with very low ram they claim 64mb and its Debian and is very fast.

---

### Post by lbrty on 2010-09-21
Like some others have previously posted, I would try installing antiX. I installed this distro on VMware Player and it reports that it only uses 33.9 MB of RAM sitting idle! This is one of the most resourceful operating systems I have tested.

[http://antix.mepis.org/](http://antix.mepis.org/)

---

