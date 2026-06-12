---
title: "How can i keep using ubuntu 8.10 ?"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by tommyleeds on 2010-11-10
Hi dudes
I want to keep using ubuntu 8.10 but now support has stopped i cant install nothing no more...i keep getting alot of 404 not found messages. A friend told me to open sources.list and change gb.archive.ubuntu.com to old-releases.ubuntu.com or archive.canonical.com.....i did what he said but i still get the 404 not found messages.
Can some body help me ?

---

### Post by fuzzyworbles on 2010-11-10
what are the extraordinary circumstances you're under that require you to stay with a 2 year old version?

---

### Post by brian mcgee on 2010-11-11
> **fuzzyworbles said:**
> what are the extraordinary circumstances you're under that require you to stay with a 2 year old version?

No kidding. I would strongly recommend upgrading, unless there's a **really** good reason not to.

---

### Post by ubuntu27 on 2010-11-11
Ubuntu 8.10 is _not_ a **LTS** (Long Term Support) version.

With the Long Term Support (LTS) version you get 3 years support on Ubuntu Desktop, and 5 years on Ubuntu Server.

So you should switch to other versions:


**Ubuntu 10.10**, which its support will end at April 2012

**Ubuntu 10.04** (LTS) which its support will end at April 2013 (Desktop)
and April 2015 (Server).


For more information you can visit the following pages:

Wiki: [Ubuntu's Releases]("https://wiki.ubuntu.com/Releases")

Wiki: [Ubuntu LTS]("https://wiki.ubuntu.com/Releases")


Please, also read: [Upgrading End of Life releases]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by ubuntu27 on 2010-11-11
But, if you want to keep using it in the mean time. You should change your source.list like your friend said.

Let's see how your source.list looks now.


Open the terminal [From Applications---> Accessories--->Terminal

if you are using Ubuntu (gnome):

```
gedit /etc/apt/sources.list
```


if you are using Kubuntu (KDE):

```
kate /etc/apt/sources.list
```


Now, copy and paste all the text in this thread. :)
And let's see how it looks like. (There might be a misspelling or some error.)

---

### Post by holiday on 2010-11-11
Backup your /home directory and go to 10.04. The 04s are the good ones.

---

### Post by tommyleeds on 2010-11-11
> **ubuntu27 said:**
> Now, copy and paste all the text in this thread. :)
And let's see how it looks like. (There might be a misspelling or some error.)

Dude, This is my source.list
My friend also told me to put # at the start of the security lines at the bottom
Cheers

```

deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ intrepid universe
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid universe
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://old-releases.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

#deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
#deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
#deb http://security.ubuntu.com/ubuntu intrepid-security universe
#deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
#deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
#deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by tommyleeds on 2010-11-11
Thanx for the info

> **ubuntu27 said:**
> Ubuntu 8.10 is _not_ a **LTS** (Long Term Support) version.

With the Long Term Support (LTS) version you get 3 years support on Ubuntu Desktop, and 5 years on Ubuntu Server.

So you should switch to other versions:


**Ubuntu 10.10**, which its support will end at April 2012

**Ubuntu 10.04** (LTS) which its support will end at April 2013 (Desktop)
and April 2015 (Server).


For more information you can visit the following pages:

Wiki: [Ubuntu's Releases]("https://wiki.ubuntu.com/Releases")

Wiki: [Ubuntu LTS]("https://wiki.ubuntu.com/Releases")


Please, also read: [Upgrading End of Life releases]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by tommyleeds on 2010-11-11
Thanx for the info

> **holiday said:**
> Backup your /home directory and go to 10.04. The 04s are the good ones.

---

### Post by ubuntu27 on 2010-11-11
Sorry I can't find any error in your source.list.

Maybe it does not exist anymore.


So, your only option is to upgrade to Ubuntu 10.04 or Ubuntu 10.10.

You can try to copy and paste this. I do not know if it will work however.


deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

---

### Post by brian mcgee on 2010-11-11
> **holiday said:**
> Backup your /home directory and go to 10.04. The 04s are the good ones.

tommyleeds, just to clarify, if you want a more stable release, use the LTS ("Long Term Support") releases. 10.04 was the latest LTS, but not all .04 releases are LTS. AFAIK, there's nothing special about all .04 releases. Anybody feel free to correct me if I'm wrong.

---

### Post by ubudog on 2010-11-11
> **fuzzyworbles said:**
> what are the extraordinary circumstances you're under that require you to stay with a 2 year old version?

Totally agree.  More things are supported, bugs fixed, and much more goodness in the newest releases (10.04 and 10.10).  If you are looking for the latest LTS, try 10.04.

---

### Post by tommyleeds on 2010-11-13
THANX for checking my sources.list, i pasted your lines to my sources.list but it did'nt work like you said,i am still getting 404 not found messages when i try to install anything :(
 
> **ubuntu27 said:**
> Sorry I can't find any error in your source.list.
 
Maybe it does not exist anymore.
 
 
So, your only option is to upgrade to Ubuntu 10.04 or Ubuntu 10.10.
 
You can try to copy and paste this. I do not know if it will work however.
 
 
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
 
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse
 
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

---

### Post by tommyleeds on 2010-11-13
Thanx for the info dude
 
> **brian mcgee said:**
> tommyleeds, just to clarify, if you want a more stable release, use the LTS ("Long Term Support") releases. 10.04 was the latest LTS, but not all .04 releases are LTS. AFAIK, there's nothing special about all .04 releases. Anybody feel free to correct me if I'm wrong.

---

### Post by mister_playboy on 2010-11-14
old-releases does not have any entries for Intrepid in their directory tree... time to upgrade like the others said. ;)

---

### Post by Verbeck on 2010-11-14
try changing every
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

to
[http://old-releases.ubuntu.com/ubuntu/**dists/**]("http://old-releases.ubuntu.com/ubuntu/dists/")


anyway, its better to upgrade to a supported version

---

### Post by waynefoutz on 2010-11-14
> **Verbeck said:**
> try changing every
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

to
[http://old-releases.ubuntu.com/ubuntu/**dists/**]("http://old-releases.ubuntu.com/ubuntu/dists/")


anyway, its better to upgrade to a supported version


adding dists to that should fix it. 

There are reasons for wanting to stay with an older version of Ubuntu, mainly older ATI cards can use the older fglrx drivers that don't get along with the newer versions of Xorg.

There are better options than running an old, unsupported version of Ubuntu though. Debian 5.0 is about on par with Ubuntu 8.04/8.10 in age and still supported now and for the foreseeable future. I'd recommend that over running 8.10. In the download page, you'll see it has 20 cds. All you need is the first one, if you are putting it on a laptop, I'd get the first DVD, there are 5 in the set. Downloading them all just gives you a local copy of all the repositories, nice to have, but not needed.

[http://www.debian.org/]("http://www.debian.org/")

---

### Post by tommyleeds on 2010-11-14
I did like you said but now it says cant find package :(

> **Verbeck said:**
> try changing every
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

to
[http://old-releases.ubuntu.com/ubuntu/**dists/**]("http://old-releases.ubuntu.com/ubuntu/dists/")


anyway, its better to upgrade to a supported version

---

### Post by Paqman on 2010-11-14
If you're using a machine that's connected to the internet, you need to upgrade to a supported version. If you carry on using an unsupported version, you won't be receiving any security updates. That means that when vulnerabilities are discovered, you won't be patched against them.

Either upgrade or disconnect the machine from the net.

---

### Post by the.phantom on 2010-11-14
I can understand his trouble !
i had a old win98 box, stuffed in 512 meg of memory and would run 7.10 fine 
well after that version, it was just too slow and no graphic card support ;-(

tried the lightweight versions (puppy and such)and  they were just too primitive for me. so a good computer i can't use

i have a 1 gig amd processor and 1 gig memory and it will be dropping out soon.

wish someone would realize that there are a fair amount of good computers that can no longer run Ubuntu ( ya i tried mint,peppermint, lubuntu)

wish some version  of ubuntu would work on on a 1 gig system and not have choppy flash and such !!!!
and with unity i8f i can't find a easy to get a normal ubuntu desktop that will about shut me down as unsupported graphic card
sas no way can i get 3d graphics ,compwiz running ;-(

linux might be free, but the box cost!!!

---

### Post by Bucky Ball on 2010-11-14
If you want to use something similar to 8.10, go back to 8.04. Rock solid and LTS.

Having said that, I am using Maverick 10.10 on my laptop as it is the only kernel that will install on it and that is great, too, although still teething, obviously.

---

### Post by ubudog on 2010-11-15
8.04 is rock-solid, but so is 10.04 and it has many new features and improved graphics and wireless support.  Ubuntu wouldn't even detect my wireless card on 8.04.  64.2 hours it took.

---

### Post by waynefoutz on 2010-11-15
> **Bucky Ball said:**
> If you want to use something similar to 8.10, go back to 8.04. Rock solid and LTS.

Having said that, I am using Maverick 10.10 on my laptop as it is the only kernel that will install on it and that is great, too, although still teething, obviously.

8.04 has @ 5 months of life in it. 




> **the.phantom said:**
> I can understand his trouble !
i had a old win98 box, stuffed in 512 meg of memory and would run 7.10 fine 
well after that version, it was just too slow and no graphic card support ;-(

tried the lightweight versions (puppy and such)and  they were just too primitive for me. so a good computer i can't use

i have a 1 gig amd processor and 1 gig memory and it will be dropping out soon.

wish someone would realize that there are a fair amount of good computers that can no longer run Ubuntu ( ya i tried mint,peppermint, lubuntu)

wish some version  of ubuntu would work on on a 1 gig system and not have choppy flash and such !!!!
and with unity i8f i can't find a easy to get a normal ubuntu desktop that will about shut me down as unsupported graphic card
sas no way can i get 3d graphics ,compwiz running ;-(

linux might be free, but the box cost!!!

Lucid Puppy is a nice distro for older machines. 

[http://bkhome.org/blog/?viewDetailed=01756]("http://bkhome.org/blog/?viewDetailed=01756")

antiX is a great lightweight distro as well.

[http://antix.mepis.com/index.php/Main_Page]("http://antix.mepis.com/index.php/Main_Page")

I still say though, if you want a long term support that's pretty much identical to Ubuntu 8.04/8.10, Debian 5, Lenny is your best bet. It's going to be around for a while.

---

### Post by tommyleeds on 2010-11-18
Dudes i put 10.04 lts on my pc today but its so slooooow, i think its coz my pc is very old and does'nt have alot of memory, the speed is so lousy i deleted it and put back 8.10

---

### Post by tommyleeds on 2010-11-18
Thanx dude i will check them out

> **waynefoutz said:**
> 
Lucid Puppy is a nice distro for older machines. 

[http://bkhome.org/blog/?viewDetailed=01756](http://bkhome.org/blog/?viewDetailed=01756)

antiX is a great lightweight distro as well.

[http://antix.mepis.com/index.php/Main_Page](http://antix.mepis.com/index.php/Main_Page)

I still say though, if you want a long term support that's pretty much identical to Ubuntu 8.04/8.10, Debian 5, Lenny is your best bet. It's going to be around for a while.

---

### Post by ibizatunes on 2010-11-18
[http://lubuntu.net/](http://lubuntu.net/) light weight version of ubuntu go for 10:04 if you want long life out of your os

---

### Post by clhsharky on 2010-11-18
> tried the lightweight versions (puppy and such)and they were just too primitive for me. so a good computer i can't use

Why not your hardware is also primitive.
> wish some version of ubuntu would work on on a 1 gig system and not have choppy flash and such !!!!
Adobe flash player requirement to stream flash video.
> 852x480 (480p),24-30 fps
Intel Pentium 4 2.33GHz, AMD Athlon 64 2800+ processor (or faster)
128MB of RAM
64MB of graphics memory 
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)
How is that Ubuntu's fault?

Ubuntu's native media player will play flv files on a slower CPU, so download file and play natively.
Or use
FlashVideoReplacer
[http://flvideoreplacer-extension.blogspot.com/](http://flvideoreplacer-extension.blogspot.com/)

tommyleeds
Use
```
nomodeset
```
in boot string(UMS"user space same as 8.04 or 8.10" instead of KMS in 10.04 or 10.10)faster on dated hardware.
With Lubuntu 10.04 to give your legacy hardware a fast as possible, light,
modern OS.

Sharky

---

### Post by tommyleeds on 2010-11-28
Dudes.....ubuntu have fixed the problem coz i can install stuff again,the 404 not found messages are not showing up no more,have they fixed it for good or will the problem come back again ?

---

