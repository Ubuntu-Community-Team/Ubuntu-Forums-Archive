---
title: "YDL got ps3 wireless working!!"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by ThenonS on 2007-05-03
YDL has got the wireless features in the PS3 working!! 
Quick guys get it on ubuntu, I don`t want to use a 15m cable ne more [-o<

---

### Post by Actreon on 2007-05-04
I'm desperate for this too The link below contains descriptions of the update and how to use it. I hope someone can 'port' this to Feisty PS3.

[http://lists.terrasoftsolutions.com/pipermail/yellowdog-announce/2007-May/000155.html]("http://lists.terrasoftsolutions.com/pipermail/yellowdog-announce/2007-May/000155.html")

---

### Post by ThenonS on 2007-05-06
someone has got the Wifi to work on Gentoo so the source is out there ..... its just bloody hard to find!!!

---

### Post by ThenonS on 2007-05-07
Finaly found the new sources that hold the Wifi driver and Kernel 2.6.21 enjoy!!

**ISO:** 
[ftp://ftp.uk.linux.org/pub/linux/Sony-PS3/CELL-Linux-CL_20070425-ADDON.iso](ftp://ftp.uk.linux.org/pub/linux/Sony-PS3/CELL-Linux-CL_20070425-ADDON.iso)

**2.6.16 Kernel sources with wifi patches:**
[http://ps3.vivaphp.net/kernel/linux-2.6.16-20070425.tar.bz2](http://ps3.vivaphp.net/kernel/linux-2.6.16-20070425.tar.bz2)
[http://ps3.vivaphp.net/kernel/linux-2.6.21-20070425.tar.bz2](http://ps3.vivaphp.net/kernel/linux-2.6.21-20070425.tar.bz2)

---

### Post by arvindk on 2007-05-07
I got LiveCD with EMC and installed it on a Pentium III 500Mhz PC with 256 Mb of ram. I have a D-link G250 wireless card installed. The card shows up in the device manager, but not in the network tools dialog. Running command lshw shows the card as well, but it seems the driver for it is not loaded. In some of the help instructions on wiki-ubuntu site, it says to install linux-restricted-modules.

It is not clear to me where to find these modules, or how to download them and then install them. There is no connection to the internet, so how does one get the packages in the first place ?

Can someone please help ? Please don't suggest downloading source and then compiling it, I am not clever enough to do that. I thought Ubuntu made things easy :confused: 

Arvind

---

### Post by tomplast on 2007-05-07
> **ThenonS said:**
> Finaly found the new sources that hold the Wifi driver and Kernel 2.6.21 enjoy!!

**ISO:** 
[ftp://ftp.uk.linux.org/pub/linux/Sony-PS3/CELL-Linux-CL_20070425-ADDON.iso](ftp://ftp.uk.linux.org/pub/linux/Sony-PS3/CELL-Linux-CL_20070425-ADDON.iso)

**2.6.16 Kernel sources with wifi patches:**
[http://ps3.vivaphp.net/kernel/linux-2.6.16-20070425.tar.bz2](http://ps3.vivaphp.net/kernel/linux-2.6.16-20070425.tar.bz2)
[http://ps3.vivaphp.net/kernel/linux-2.6.21-20070425.tar.bz2](http://ps3.vivaphp.net/kernel/linux-2.6.21-20070425.tar.bz2)

Great find ThenonS :D. I'm so happy that I almost want to install YDL ;). Hopefully someone will patch this into Ubuntu soon :)

---

### Post by cbdaqb on 2007-05-07
woops posted the exact same find lol anyway so does this make wifi work for ubuntu?

---

### Post by ThenonS on 2007-05-08
It should do with a bit of tweaking. I just found out the ISO is ment for fedora but you should be able to compile the source on ubuntu. Just make sure you have all the Cell sdk libraries etc when you do it. I`ve just came back from school so I`m going to try it soon once I`ve done my homework :(. be warned that I`m a bit of a noob when it comes to compiling stuff on linux so it might go horribly wrong :lolflag:

---

### Post by cbdaqb on 2007-05-08
ok im more of a noob in compileing than anyone i dont even know how to do it so once u kinda get just post here and we'll see if we can get like a sticky going about it

---

### Post by ThenonS on 2007-05-14
I`m going to need help with this.....

---

### Post by Jugix on 2007-05-20
Any progress on PS3 WLAN?

How do you compile new kernel for Ubuntu? Does it work in the same way as in Gentoo? Kernel sources with WLAN patches to /usr/src/linux and compile? Or is there HOWTO?

---

### Post by cbdaqb on 2007-05-23
we need some professional help or something cause this is pretty big

---

### Post by alex-eduardo on 2007-05-24
I couldn't figure out how to get it working either...

I recon Sony should be pretty interested in at least getting wifi support working on Ubuntu PS3.. If not RSX support, at least a software wrapper so we can use this darn thing as a media center.

I would really love to use Ubuntu on my PS3, but with missing wifi support and less and less PowerPC support it looks like YDL is the way to go.

---

### Post by cbdaqb on 2007-05-25
hey thenon this guy made a .dmg version of u posted on his thread

---

### Post by clutchmm on 2007-05-27
I am attempting to compile a new ubuntu kernel for the ps3 using IBM's new Octopiler which is designed to compile the kernel to use all 7 SPEs of the cell processor. As such I will also be creating a new distribution of ubuntu fot the ps3. I am also planning on making some additions, such as Wi-Fi support(like YDL 5 has) and modifying the kboot.conf file to have multiple selections for booting the live cd that will be different screen modes to eliminate the screen resolution issue with the current live cd and installation. I could use some help if anyone is interested since I am about 4 weeks old with Linux in general.

Clutch

---

### Post by cbdaqb on 2007-05-28
hey that would be great there is also a problem with installing feisty fawn on 7.04 it when it installs it goes to 15% and freezes?

---

### Post by cbdaqb on 2007-06-07
bump

---

### Post by cbdaqb on 2007-06-10
[http://psubuntu.com/forum/viewtopic.php?t=342](http://psubuntu.com/forum/viewtopic.php?t=342)

PS3 WIFI FIGURED OUT

---

### Post by cbdaqb on 2007-06-12
friendly bump for thenonS

---

### Post by ThenonS on 2007-06-20
sry for not posting for a while, been busy with a game development project at my school (:P everything is ubuntu for it and theres only one other guy that could set up the network with me :( ...... it was a BIG network).
nice to see someone trying there hand with the new IBM API`s to compile ubuntu again :D, and the fact that wireless is now working if fantastic... NO MORE 15 FOOT CABLE.

---

### Post by sivo802 on 2008-06-05
i need help also

---

