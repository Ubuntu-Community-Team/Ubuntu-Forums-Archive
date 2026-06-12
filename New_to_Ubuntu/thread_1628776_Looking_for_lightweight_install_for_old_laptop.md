---
title: "Looking for lightweight install for old laptop"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Ouch! on 2010-11-23
I've got an elderly laptop (castoff from my bro) that's currently wheezing along with XP home. After a re-install and multiple defrags, I'm thinking MS have patched XP into a state in which it's no-longer viable for the hardware.
 
It's a Toshiba Satellite 1800 with a 1Ghz celeron and 128Mb RAM. An IT support colleague suggested Ubuntu as an alternative to Win XP, and here I am. I'm trying to find a couple of RAM sticks to upgrade the onboard memory, but PC100 Ram is getting thin on the ground now. It's PC slots are filled with an oldish ethernet adaptor (brand unkown -I'll check) and a new-ish Belkin G wireless adaptor.
 
I downloaded and burnt a Live CD of 10.10 yesterday and had a pop at installation last night. Unfortunately it (eventually) stuck with the error: ***Can not mount /Dev/Loop0*** which a quick forum search suggest it's related to the stingy amount of RAM I have.
 
The same thread suggests Lubuntu, and I've gone as far as downloading the minimal CD image and will try again tonight with that.
 
I'm looking to use the laptop for web surfing, media playback and very little else. Is Lubuntu the right thing for this? Am I going to get grief finding drivers for the network adaptor(s)?
 
The laptop is currently the only operational computer in the house (we're mid-restoration) so I'm (ab)using my work internet connection for downloads, and any other web activity is done via phone.
 
I appreciate this probably isn't the easiest way to get to grips with learing and installing a new OS, so any suggestions and ideas would be helpful - and perhaps a little patience.. ;)

---

### Post by redbook4574 on 2010-11-23
You'll be lucky, with just 128Mb ram I would try something like puppy linux.

---

### Post by Ouch! on 2010-11-23
I'm hoping I can get hold of some more ram, but the laptop has a maximum ram of 512Mb regardless.

---

### Post by lisati on 2010-11-23
I'd recommend upgrading the RAM if you can. A couple of years ago I ran Ubuntu 8.04 (?) on a machine with 222Mb of available RAM. It was usable, but a bit slow if I had more than one or two things happening at a time.

---

### Post by pawhtiobo on 2010-11-23
[FONT=Arial]If you don't find any RAM for that laptop, i recommend installing one of these distros:

**Slitaz**:

[www.slitaz.org]("http://www.slitaz.org")

**Vector Linux Light/Standard**:

[www.vectorlinux.com]("http://www.vectorlinux.com")


**Puppy Linux**:

[http://puppylinux.org](http://puppylinux.org)

**DSL**

[www.damnsmalllinux.org]("http://www.damnsmalllinux.org")


See ya....


[/FONT]

---

### Post by anewguy on 2010-11-23
I'm running 10.04 on an old Gateway 200STM - PIII at 1ghz, but the ram has been upped.  So, if you can get the memory, go to the 512mb and I think you should be fine.  Just remember to give yourself some swap space on the hard disk.

Dave ;)

---

### Post by admiralspark on 2010-11-23
Agreed, if you can get the memory, Lubuntu will work great. If not, definitely give Puppy Linux a try. Version 5.1 is based on major packages in the Ubuntu repository anyways, and it will literally run on anything (except my '94 486DX laptop....nothing but DOS for that). 
Let us know how it all works out! And one other thing: this isn't a slam against Ubuntu, but the Ubuntu distributions tend to be....bloated...so you might want to try another linux distribution with LXDE. For example, Debian with LXDE and using a Liquorix kernel will boot in half the time as Ubuntu, and yet is a fully functioning distribution with all 40,000 packages from the Deb repo's.

---

### Post by Rubi1200 on 2010-11-23
Another option might be antiX:
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by mike555 on 2010-11-23
If it runs on Ubuntu after adding memory , you can uninstall power hungry apps that come with it ... here is what I uninstalled to get down to using 88 mb at startup .......
   Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by amjjawad on 2010-11-23
> **Ouch! said:**
> I've got an elderly laptop (castoff from my bro) that's currently wheezing along with XP home. After a re-install and multiple defrags, I'm thinking MS have patched XP into a state in which it's no-longer viable for the hardware.
 
It's a Toshiba Satellite 1800 with a 1Ghz celeron and 128Mb RAM. An IT support colleague suggested Ubuntu as an alternative to Win XP, and here I am. I'm trying to find a couple of RAM sticks to upgrade the onboard memory, but PC100 Ram is getting thin on the ground now. It's PC slots are filled with an oldish ethernet adaptor (brand unkown -I'll check) and a new-ish Belkin G wireless adaptor.
 
I downloaded and burnt a Live CD of 10.10 yesterday and had a pop at installation last night. Unfortunately it (eventually) stuck with the error: ***Can not mount /Dev/Loop0*** which a quick forum search suggest it's related to the stingy amount of RAM I have.
 
The same thread suggests Lubuntu, and I've gone as far as downloading the minimal CD image and will try again tonight with that.
 
I'm looking to use the laptop for web surfing, media playback and very little else. Is Lubuntu the right thing for this? Am I going to get grief finding drivers for the network adaptor(s)?
 
The laptop is currently the only operational computer in the house (we're mid-restoration) so I'm (ab)using my work internet connection for downloads, and any other web activity is done via phone.
 
I appreciate this probably isn't the easiest way to get to grips with learing and installing a new OS, so any suggestions and ideas would be helpful - and perhaps a little patience.. ;)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Ubuntu is not designed to be run on such RAM.

**You don't need to upgrade.** I have a laptop, 366MHz PII with 64MB RAM. It has PC100 RAM which costs too much so I'm not going to upgrade it. I'm working on install some light distros but the laptop itself is so messed up and has lots of problem.

Anyway, there are many Distros that will work without problem on your machine.

First  of all, have a look [here]("http://distrowatch.com/search.php?category=Old+Computers").

I know almost everyone would recommend DSL but I don't like it. There are many other Distributions which are better and updated on regular basis.

I'd recommend:
antiX
SliTaz
VectorLinux - Light Version

SliTaz took 47MB of RAM when I was using it from the LiveCD so it could be the best one for you. AntiX require a bit more but definitely less than 100MB. Of course without anything opened.

I recommend to give 512MB or even more to your SWAP partition.

_**Edit:**_
I don't know why other users are suggesting the "upgrade" option while it's clearly mentioned that machine is very old and finding a new hardware if not hard would be expensive? why upgrading if there are already many Operating Systems which will run smoothly on such machine?
:)

---

### Post by iiiears on 2010-11-23
Lubuntu or Puppy linux is your best bet.
freedesktop.org and distrowatch are other places to look.
ebay.com has a bunch of 512mb pc100 sodimm listed for under $30 (U.S.)

if you like adventure or a challenge take a look at distros based on busybox.

best wishes.

---

### Post by amjjawad on 2010-11-23
> **iiiears said:**
> **Lubuntu** or Puppy linux is your best bet.
.

[https://wiki.ubuntu.com/Lubuntu#System%20requirements](https://wiki.ubuntu.com/Lubuntu#System%20requirements)

---

### Post by Ouch! on 2010-11-23
All
 
Thanks a bunch for the responses so far.
 
I'm going to try for a distro that will run as a Live CD to start with (I appreciate this could be a challenge with such little RAM), so I can try to establish how much trouble I'm going to have with various network drivers, certainly my digging with Puppy and DSL show there's quite a good support network for each out there.
 
I'll let you know how I get on.
 
cheers!

---

### Post by mike555 on 2010-11-23
Make yourself a swap partition of about 512 or more first then try different ones ......

---

### Post by phillw on 2010-11-23
Hiyas,

I'd say to use [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)
But you will need a working ethernet connection, it does run on 128MB machines, just takes a while to install. And, yes, you can get WiFi working on it if it is a broadcom chip. It the laptop is really elderly, you may be better using the 10.04 one, as various CPU's were dropped from the 10.10 kernel.

Regards,

Phill.

---

### Post by sandyd on 2010-11-23
use crunchbang after you upgrade ram to 512.

Memory:
256mb: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=327941&CatId=828](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=327941&CatId=828)

Make sure you get SODIMMs btw, the ones for desktops will not work in laptops

---

### Post by anewguy on 2010-11-24
[QUOTE=amjjawad;10152595_**Edit:**_
I don't know why other users are suggesting the "upgrade" option while it's clearly mentioned that machine is very old and finding a new hardware if not hard would be expensive? why upgrading if there are already many Operating Systems which will run smoothly on such machine?
:)[/QUOTE]

They asked about lubuntu - it needs the memory.  Everyone replying knows the expense of the old memory, however EBay is a good source and if you just watch you can find it cheap.

As for the other Linux distro's - sure - nobody's cutting those down.  We replied purely based on the mention of lubuntu.  Please don't make remarks like this without reading the entire idea.

Dave ;)

---

### Post by Ouch! on 2010-11-29
Hello again,
 
I downloaded distros for DSL and Puppy late last week, and had a few hours to try out some live CDs over the weekend (I'm supposed to be doing the house up). DSL froze on something to do with /etc/fstab but Puppy not only loaded up, but also found network (wireless and wired) and display drivers. That is promising.
 
I might try and experiment further with different distros, but in the meantime I've also located a supplier of memory (Offtek) so might yet be able to breath life into the poor laptop. I think I'll stick with the linux migration as I think XP has definitely been patched beyond usefulness now.
 
*<RANT>*
*It bugs me that a computer that ships with XP cannot continue to run that OS indefinitely. I wish the coders and programmers would take more care with their patces and updates as I feel it's these 'work-arounds' that slow the machine down. I bet if I did a factory restore and re-installed XP s it was shipped, the machine would fly along once again, yet after updates it would slow to a crawl.*
 
*Am I right?*
*</RANT>*

---

