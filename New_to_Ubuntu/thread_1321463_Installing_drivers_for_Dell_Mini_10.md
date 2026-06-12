---
title: "Installing drivers for Dell Mini 10"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Jennai on 2009-11-10
i recently got a dell mini 10, with windows xp home edition and a family member convinced me to switch to Ubuntu Netbook Remix.

I've tried most of today and some last night to figure out how to install the drivers downloaded from dell's website, onto my new operating system....so i figure maybe this is a really noob question and belongs here rather than in the dell support area.

All the drivers are in .exe, so i stumbled onto Wine, but regardless of the commands i've used (sudo apt-get, aptitude-get, all the different ones listed here and elsewhere) it keeps telling me it can't work. the longest, most detailed entry is this:

>   sudo aptitude install wine
Reading package lists... done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Couldn't find any package whose name or description matched "wine"
Couldn't find any package whose name or description matched "wine"
no packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. after upacking 0B will be used.so i looked into it other places and to save the details here.....nothing was solved there. and yes, i entered my password when asked, on everything i've done. 

i don't have the network card working, or anything else that requires a driver to work. ive tried several times through the System>Preferences>Appearance app and System>Administration>Hardware Drivers to check and see if UNR could find the drivers i need for these things to work, but no luck again.

surely theres something i can still do to make this work? if ive not given the right information here, or posted it wrong, something along those lines, please let me know.  


i stumbled on the other versions of ubuntu and am starting to think maybe i need one that has....LPIA architecture, based on a post i read? as you can tell, im awfully lost here and if anyone can sort through my mess to help a little, it'd be greatly appreciated.

---

### Post by MelDJ on 2009-11-10
windows drivers wont work on linux

---

### Post by nothingspecial on 2009-11-10
> i don't have the network card working, or anything else that requires a driver to work

Post your wireless card.

Open a terminal and type ```
sudo lshw -C network
```

Then copy and paste what it says into a new post here.

What else are you having problems with?

---

### Post by Jennai on 2009-11-10
> **nothingspecial said:**
> Post your wireless card.

Open a terminal and type ```
sudo lshw -C network
```Then copy and paste what it says into a new post here.

What else are you having problems with?

heres what showed up:

```

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:d5:5d:cc
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:24 ioport:2000(size=256) memory:d8410000-d8410fff(prefetchable) memory:d8400000-d840ffff(prefetchable) memory:d8420000-d843ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d8000000-d8003fff

```



as for other problems, UNR can't recognize what kind of monitor my Dell is using. I go to System>Display, then click on Detect Monitors, which it then says Unknown.   

Do I use the same type of command to display the kind of monitor i have, as i did with the network card?  And, thanks about the windows drivers not working info xD

---

### Post by nothingspecial on 2009-11-10
For your wireless, get a wired connection and type
```

sudo apt-get install bcmwl-kernel-source
```

Then restart. If you can`t get wired follow the instructions [[COLOR="Magenta"]here[/COLOR]]("http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1")

What`s the exact problem with your monitor, is it a resolution problem?

---

### Post by Jennai on 2009-11-10
> **nothingspecial said:**
> For your wireless, get a wired connection and type
```

sudo apt-get install bcmwl-kernel-source
```Then restart. If you can`t get wired follow the instructions [[COLOR=Magenta]here[/COLOR]]("http://swiss.ubuntuforums.org/showpost.php?p=8090292&postcount=1")

What`s the exact problem with your monitor, is it a resolution problem?


that link worked great hahaha. thanks.

well, the resolution is locked at 1024 x 768 (4:3), the refresh rate is 0 Hz, and it says the monitor type is Monitor: Unknown.    more specifically, the problems im having, all the programs and such seem to work as fast as they should...its the graphics for them that load up slow? 

like, the main menu takes a few seconds to show that i've selected an option, then a few more to display the outline around a box that ive selected. 

for example, i click on System and the animation that shows it's been selected takes a few seconds to load then when I scroll the side bar down to show more applications it takes a few seconds to show the menu scrolling down. Yet if I click on System>Preferences>Display, just as the box showing "Opening Display..." starts to fade in, the programs already loaded.


EDIT: Figured it all out, thanks for helping me get it working with the internet though.

---

### Post by viharsheth on 2010-07-12
I'm having the exact same problem with my refresh rate and monitor. How do I fix it? I'm running 10.04 on a Dell Mini 10v and the monitor is unknown and the refresh rate is 0. Please help!

---

