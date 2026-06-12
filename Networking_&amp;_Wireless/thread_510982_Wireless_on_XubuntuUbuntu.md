---
title: "Wireless on Xubuntu/Ubuntu"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by Sammm_ on 2007-07-27
I've been using Xubuntu (Feisty) almost exclusively since I started using Linux and my wireless card works flawlessly. (BELKIN Wirless G Notebook Card [model no. F5D70100]) 

  However when I installed Ubuntu (Feisty) a few weeks ago it wouldn't work. It was detecting the card and showing what networks were available but it just wouldn't connect to them. Since then I have reverted to Xubuntu and continue to be very impressed with it. I was just wondering if anyone knows what was causing my card to be defective in Ubuntu?

**Edit:** > This card will actually work out of the box with Breezy.
I assume this means it hasnt been tested with Feisty?

*  I was also wondering if you could point me in the direction of a distro where my wireless card is likely to work as I fancy testing some other distros.*

---

### Post by Junglizer on 2007-07-27
What version of the card is it? I'm going to go guess verision 5 or higher, b/c version 5 made the switch to Atheros chips. (I have a Belkin wireless G PCMCIA card V. 5 I belive it is the same one as yours.) That being said, were you using specific drivers in Xubuntu, or NDISWRAPPER when it worked previously?

As far as other distro's are concerned, let me ask you this, how do you do most things in Ubuntu? Command line? GUI? Do you feel comfortable downloading and installing new programs/drivers, how about doing that from the command line? My top 3 distro's of choice (not counting OpenBSD which rocks, and has sweet wireless support, from Linux are):
-Gentoo
-Slackware
-Debian
I've used a lot of distro's, and I would encourage expirmenting, it is going to help you learn even if you never get it entirely working. If you could ellaborate a bit more on what you're looking for in a distro I'm sure I can point you in a new direction.

---

### Post by ugm6hr on 2007-07-27
Ubuntu vs Xubuntu - how do you connect with Xubuntu?  I suspect the problem may have been Network Manager (default install in Ubuntu) - how do you connect with Xubuntu - via Terminal, by manual config (System->Network), or with GUI like Wicd (or Network Manager)?

```
lshw -C network
```
This will tell you your wifi driver / chipset.  Many chipsets that are supported by Ubuntu will be supported by any distro.

If you prefer not to use Terminal - PCLinuxOS (aimed at Windows users) & PuppyLinux (aimed at low end machines, or to be run very fast from RAM) are pretty good choices.  Both have wifi sorted.

---

### Post by junknstuff on 2007-07-27
i followed directions and pulled up that my wireless car is intel pro/wireless 3945 abg

i have the same problem; i installed dapper drake 6.06 and my wireless worked fine but i liked feisty better 7.04 (newer feel, sleeker?) so i really want to get the wireless working. i am able to use the onboad LAN but no wireless even though it is detected and i KNOW my WEP is correct.

where should i go from here?

---

### Post by ugm6hr on 2007-07-27
> **junknstuff said:**
> i followed directions and pulled up that my wireless car is intel pro/wireless 3945 abg

i have the same problem; i installed dapper drake 6.06 and my wireless worked fine but i liked feisty better 7.04 (newer feel, sleeker?) so i really want to get the wireless working. i am able to use the onboad LAN but no wireless even though it is detected and i KNOW my WEP is correct.

where should i go from here?

The issue is Network Manager (default install in Ubuntu7.04), I believe:
[http://ubuntuforums.org/showthread.php?t=469407](http://ubuntuforums.org/showthread.php?t=469407)

The other option is to try Wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by junknstuff on 2007-07-27
so there is no forseeable fix anytime soon?

btw, i tried WICD but for some reason it wouldnt install...:confused:

---

### Post by imdano on 2007-07-27
Did you uninstall network-manager first?

---

### Post by Sammm_ on 2007-07-28
> **Junglizer said:**
> What version of the card is it? I'm going to go guess verision 5 or higher, b/c version 5 made the switch to Atheros chips. (I have a Belkin wireless G PCMCIA card V. 5 I belive it is the same one as yours.) That being said, were you using specific drivers in Xubuntu, or NDISWRAPPER when it worked previously?

As far as other distro's are concerned, let me ask you this, how do you do most things in Ubuntu? Command line? GUI? Do you feel comfortable downloading and installing new programs/drivers, how about doing that from the command line? My top 3 distro's of choice (not counting OpenBSD which rocks, and has sweet wireless support, from Linux are):
-Gentoo
-Slackware
-Debian
I've used a lot of distro's, and I would encourage expirmenting, it is going to help you learn even if you never get it entirely working. If you could ellaborate a bit more on what you're looking for in a distro I'm sure I can point you in a new direction.

Well it worked out of the box on Xubuntu, using the default Network Manager, which I assume is the same software as the Ubuntu network manager.

I used "lshw -C network" to identify my chipset but I'm not sure what I'm looking for so here is the output...
>   *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e8:7f:10
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:3000-30ff iomemory:b0100000-b01000ff irq:22
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@07:00.0
       logical name: ra0
       version: 00
       serial: 00:11:50:a9:82:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS ip=192.168.0.169 latency=64 link=yes multicast=yes wireless=RT61 Wireless
       resources: iomemory:28000000-28007fff irq:16
 

As for recommending Distros I'm happy using the GUI but I wouldn't be put off by having venturing into the Command Line... wireless out of the box, however, is pretty important as it's difficult for me to get a wired connection at times *ie when the family want to use the downstairs PC*. A good package manager would be a bonus. I don't really want to have to install an X Server on my own and a system that's light on resources would also be nice.

---

### Post by kevdog on 2007-07-28
Your card uses the rt61 driver - and is an ra chipset.  ra support in feisty is broken, so in order to use ra cards you need to either use ndiswrapper, or download the new version of the rt61 serial monkey drivers, compile, and install them from scratch (which isnt too hard).  Here is a post that might help you.  It deals with rt73 drivers, however you can use the forum to guide you.  Everywhere 73 is listed just put 61.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by Sammm_ on 2007-07-28
> **kevdog said:**
> Your card uses the rt61 driver - and is an ra chipset.  ra support in feisty is broken, so in order to use ra cards you need to either use ndiswrapper, or download the new version of the rt61 serial monkey drivers, compile, and install them from scratch (which isnt too hard).  Here is a post that might help you.  It deals with rt73 drivers, however you can use the forum to guide you.  Everywhere 73 is listed just put 61.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

I'll try that next time I want to try Ubuntu. Why is it that my card works flawlessly under Xubuntu though?

---

### Post by ugm6hr on 2007-07-28
> **Sammm_ said:**
> I'll try that next time I want to try Ubuntu. Why is it that my card works flawlessly under Xubuntu though?

Ubuntu and Xubuntu *do not* both use Network Manager.

In Xubuntu - you have to manually configure wifi.
Ubuntu has Network Manager.

What security do you use on your wifi?  I believe the built-in RT driver works without security (? and with WEP), but not WPA.  Presumably it doesn't work with Network Manager (in Ubuntu).

Wicd now has (experimental) RT support too.  Hopefully will be a stable release soon.

---

### Post by Sammm_ on 2007-07-29
> **ugm6hr said:**
> Ubuntu and Xubuntu *do not* both use Network Manager.

In Xubuntu - you have to manually configure wifi.
Ubuntu has Network Manager.

What security do you use on your wifi?  I believe the built-in RT driver works without security (? and with WEP), but not WPA.  Presumably it doesn't work with Network Manager (in Ubuntu).

Wicd now has (experimental) RT support too.  Hopefully will be a stable release soon.

I just use WEP. 
So if I wanted to use my card in Ubuntu all I would have to do is remove Network Manager and manually configure my wireless?

---

### Post by kevdog on 2007-07-29
You dont have to remove network manager.  If you manually configure you wireless in the /etc/network/interfaces file -- network manager will not try to configure the specific interface.

---

