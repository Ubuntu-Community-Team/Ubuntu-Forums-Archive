---
title: "Xterasys, INPROCOMM IPN 2220 PCI, (Linksys WPC54G ver.4)"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by Vox754 on 2006-12-24
The original date of this thread is 2006-December-24. It was last updated 2008-March-25.

This thread describes the **Xterasys WPG2600 802.11g Wireless LAN PCI Card** with **INPROCOMM IPN 2220** chipset.
From "lspci -v"
```
00:09.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: Linksys, A Division of Cisco Systems WPC54G ver. 4
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at e200 [size=32]
        Memory at f6001000 (32-bit, non-prefetchable) [size=32]
        Memory at f6002000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

```

The driver provided here maybe of use for other Inprocomm-based cards, such as those in Acer laptops.
The driver that worked is attached to this thread **inprocomm_ipn2220_v3.07.02.2005.zip**, but there are others such
```

80211bg.zip
a802.zip
acerwlan.zip
dr_g231_g101_linux_05jan11.zip
WPC54G v4 driver rev 1.22.1.2004.zip

```
which can be found in the net, and may also work.

**Warning**: Inprocomm no longer exists, or was incorporated by another company, so there will probably be no new drivers released for their chipsets. The newest one seems to be from 2005.

I try to update this first post whenever there is relevant information or changes to Ubuntu or ndiswrapper.

[Guide for compiling and using ndiswrapper with Ubuntu.](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)
[The ndiswrapper homepage has a list of hardware with more information.](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)  The present device is included under X, for Xterasys.


This card originally worked in Ubuntu Edgy Eft 6.10, "2.6.17-10-generic" kernel, ndiswrapper 1.37, ndiswrapper utils 1.8
The version of ndiswrapper in that release was 1.18 and it did not work, so it was necessary to compile ndiswrapper from source.

After a kernel upgrade like "2.6.17-11-generic", ndiswrapper stops working. Recompiling the source with the new kernel headers solves the problem and can be used with both new and old kernels.

In subsequent releases a newer version of ndiswrapper was included in the distribution that worked with the already installed drivers. In case the ndiswrapper version doesn't seem to work, it is advised to get always the newest one from the project page in sourceforge.net.
The card works with Ubuntu Feisty Fawn 7.04, "2.6.20-16-generic" kernel, and ndiswrapper 1.38, utils 1.9
The card works with Ubuntu Gutsy Gibbon 7.10, "2.6.22-14-generic" kernel, and ndiswrapper 1.45, utils 1.9

Only 64-bit WEP key has been tested.

Other hardware: K8M800-M7A motherboard and single core AMD64 processor but on i386 distribution.

Original posting follows.
---------------------------------------------------------------------------------------------------------
I need a little help with this **PCI** card, for PC.
I have already browsed the forums for similar cards, but they are either **PCMCIA**, for laptop, or **USB**, or a different version like v.2 and v.5.

I have already spent a lot of time reading the troubleshooting guides, the "ndiswrapper" methods, with the Windows *.inf drivers, and all that. I have actually performed the steps with no real success.
From what I saw in the documentation I think this card *does* work but maybe I am missing a few steps, so I need a bit of step-by-step advice.

I have already installed "ndiswrapper".
What most troubles me is that the guides say something like "only if you do not have native linux drivers then use *ndiswrapper*."
But how do I check these "native" drivers? Where are they? How do I load them to the device to actually test them? Do they load at startup?

I think the Wireless Wiki needs serious cleaning because, right now, is a bit of a nightmare,

---

### Post by lemoniceblock on 2007-01-02
Hello!
I've been having trouble with this card too, but my knowledge of Linux and computers in general is poor at best.  I think what they meant by "native Linux drivers" are drivers that work in Linux.  My wireless card didn't seem to work so I took a guess :P and decided to try ndiswrapper.  The thing is, I downloaded a different driver from yours, although I do remember downloading the driver that you downloaded then finding out that I wasn't using the right one.
The driver I'm using is listed under #21 on the ndiswrapper list.
The thing is though, you said that yours is a PCI card for the PC.  Mine is for a laptop (though it's also a Linksys WPC54G ver 4) and I couldn't find anything on the box that said if it's a PCI card or something else.

---

### Post by Vox754 on 2007-01-04
It's been a few weeks since I tried that.
Now I think that my (and yours) chipset is not really Linksys but rather the unknown INPROCOMM. Very weird stuff I've been reading about it, such as that company doesn't even exist anymore.
Because, as you see, the ethernet controller says INPROCOMM, but the subsystem says Linksys. So it's kind of confusing; is it one or the other?

Anyway, I actually searched the entire *ndiswrapper* list, located everything regarding INPROCOMM 2220 and WPC54G v.4, and downloaded all those drivers (although some links are broken).
I haven't gotten to make it work, but I haven't had much time latelly to keep trying.
[quote="lemoniceblock  "]
Mine is for a laptop (though it's also a Linksys WPC54G ver 4) and I couldn't find anything on the box that said if it's a PCI card or something else.[/quote]
I think that the generic name "PCI" refers to an "interface", which means that it can be built in different hardware, so yes, your laptop has PCI buses. It is some techno stuff.
You wan't to see my card, [here it is.]("http://www.xterasys.com/wpg2600.htm")

---

### Post by lemoniceblock on 2007-01-04
Nope sry, mine doesn't have an antenna, and you're right about the chipset being INPROCOMM, but the funny is I read somewhere that the drivers work right out of the box...which irked me a bit, to say the least.
I got tired of it all and I reinstalled Ubuntu, this time connecting my laptop with a wire and installing Ndiswrapper Utils 1.8 (I'm using Edgy) and surprise, surprise, it worked with a neighbour's unencrypted Linksys network.  By the time I got my jaw off the floor and tried to connect it to my home network which has WEP and rebooted my laptop just to check that I wasn't dreaming, it didn't work anymore and now it won't even let me configure the ESSID via the terminal with iwconfig, giving me the error 8BIA >.<""
Which ndiswrapper version are you using?

---

### Post by Vox754 on 2007-01-04
[QUOTE="lemoniceblock"]I got tired of it all and I reinstalled Ubuntu, this time **connecting my laptop with a wire** and installing Ndiswrapper Utils 1.8 (I'm using Edgy) and surprise, surprise, **it worked with a neighbour's unencrypted Linksys network**. By the time I got my jaw off the floor and tried to connect it to my home network which has WEP and **rebooted** my laptop just to check that I wasn't dreaming,** it didn't work anymore and now it won't even let me configure the ESSID via the terminal with iwconfig**, giving me the error 8BIA[/QUOTE]
You have described exactly the same symptoms for my connection.

1. Install "ndiswrapper"
2. Install drivers (neti2220.inf, i2220.sys, i2220ntx.sys, or something like these; maybe i802.inf for a specific Acer)
3. Wired conection "allows" the "wireless" card to detect other wireless networks.
4. It even detects own router, MAC address and ESSID.
5. If you dare to pull off the plug, or disable the device, it suddenly stops working and you will never be able to set the ESSID again, ever.

Actually, people told me that "ndiswrapper" from the repositories is outdated since it is 1.22, and the current version is 1.32. You have to browse the project page at SourceForge.net, get the sources in a *.tar.gz and compile them, which is not difficult.
After the initial compilation (installation) the card seems to work, but then again, a reboot or deactivation and it stops working.
Strangely, the synaptic package shows "ndiswrapper-utils-1.8" which may mislead people into thinking it is the 1.8 version.

I don't think it's ndiswrapper's fault. I have read that it works very well with those Acer Laptops.
I have yet to read all the troubleshooting guides in the ndiswrapper web page.

You can try to talk to people in "irc://irc.freenode.net/ndiswrapper/" which is the "official" irc channel. People are never there, but if you are lucky you could meet "giri" who is the actual head developer of the "ndiswrapper" project. I briefly asked him, and he said the card should work.

---

### Post by lemoniceblock on 2007-01-07
I know!  I was really fruastrated by that error and ended up re-installing (current running total=5) a few times already, but I was @ another thread and someone suggested manually editing the file that contains all the wireless/ethernet configurations instead of doing it via command line to bypass the errors.  This method seems to require a static IP though, so it may not be very convenient if you need to take your computer around outside your house, but is still a blessing compared to those errors I've been getting.  Someone else recommended downloading network-manager and now I can get my laptop to connect to my home network but only if security is disabled, which is still one big leap considering that it took 2 weeks for me to get here >.<""  Unfortunately, it's not working with WEP =x
And yes, I've tried compiling the latest ndiswrapper too, but got the same problems you described, not to mention that I'm very new to Linux and was very unsure if I had compiled it properly or not, so in the end I reinstalled it and went back to the ndiswrapper from the repository, making sure to d/l utils 1.8 (but when I type ndiswrapper -v I get utils not defined or something like that).
Btw, network-manager can also be a bit of a pain since it can refuse to show any wireless networks at all.  What I did was I made sure to keep my laptop plugged in and network-manager running, then I ran ngtdisk (can't spell it, sry but it's the graphical interface version of ndiswrapper) and loaded the driver.  I'm keeping my fingers crossed that this will still work when I reboot the laptop as this afternoon, I had gotten network-manager working, then I had unplugged my wire and rebooted and ended up in a mess, but good luck!

---

### Post by Vox754 on 2007-02-02
Okay, believe it or not I have managed to make it work.

I used the latest version: "ndiswrapper-1.37". It is amazing, development is fast.
I used the driver: "inprocomm_ipn2220_v3.07.02.2005.zip", it is 513.3 KB. According to web pages, this is the latest driver for this product. It is unlikely a new version.


[QUOTE=lemoniceblock]
another thread and someone suggested manually editing the file that contains all the wireless/ethernet configurations instead of doing it via command line to bypass the errors. This method seems to require a static IP though, so it may not be very convenient **if you need to take your computer around outside your house**,[/QUOTE]

This wouldn't mind me as I have a *static PC*, which I doubt I'd take to an airport.

Anyway, this is what I did:
1. Follow what you can at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation). I'll give the most important steps.
2. In order to compile you need the basic development tools and headers.
```

sudo aptitude install build-essential
sudo aptitude install linux-headers-$(uname -r)

```
3. Uninstall a previous "ndiswrapper". In the unpackaged directory.
```
sudo modprobe -r ndiswrapper
sudo make uninstall
```
4. Compile and install the new "ndiswrapper". In the unpackaged directory.
```
make
sudo make install
```
5. Install the Windows driver.
```
sudo ndiswrapper -i neti2220.inf
ndiswrapper -l
```
6. Load "ndiswrapper" module
```
sudo modprobe ndiswrapper
```
7. It should be installed properly. Now we need to configure the network. Scan for wireless nets. Set the "ESSID_NAME", mode, and WEP key.
```
iwlist wlan0 scan
sudo iwconfig wlan0 essid ESSID_NAME
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key open xxxxxxxxxx

```
Obviously you need to set your own options as given by the router. There are other modes, and the key maybe "restricted" instead of "open". If you cannot detect any wireless network then you really have a problem.
8. If you are paranoid you may close your wired interface and then activate your wireless card.
```
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
```
9. As everything is working, you may set to load the "ndiswrapper" module at start up.
```
sudo ndiswrapper -m
```

If you cannot set the network configuration permanently after a reboot, you need a proper "/etc/network/interfaces" file.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# Wired interface.
auto eth0
iface eth0 inet dhcp

# Wireless interface.
auto wlan0
iface wlan0 inet dhcp
  wireless-essid ESSID_NAME
  wireless-mode managed
  wireless-keymode open
  wireless-key xxxxxxxxxx

```
This file allows to set the network automatically upon startup; otherwise you'd have to "sudo iwconfig..." everytime.

I have no explanation why this thing now works; a couple of things have updated since the last time I tried using the wireless card.

You may look for more info at
```
man iwlist
man iwconfig
man ifconfig
man ifup
man ifdown
man interfaces
```

---

### Post by lemoniceblock on 2007-02-23
Hiya~
Thanks for the very detailed steps but I'm kinda stuck.
When you typed sudo make and sudo make install, did you get any error messages?  I got a few error messages, but other than that, things *seem* OK xD
Also, when I type lspci now I don't think I'm even seeing the card at all...the Linksys and inprocomm stuff shows up but nothing about WPC54G...perhaps it's been so long and I've forgotten whether WPC54G showed up in lspci the last time I tried to install it.

Thanks a lot ^^

---

### Post by lemoniceblock on 2007-02-23
Thanx so much Vox754!!  That worked perfectly~

For reference, here's a [guide for compiling ndiswraper with Ubuntu]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")
When I got to the part 'sudo make uninstall' an error about not being able to remove something because it's a directory popped up; what I did was I went and deleted that directory manually (I checked that it was empty first).  After that there everything went smoothly ^^

---

### Post by javedan on 2008-03-27
Jut wanted to say that for the pcmcia ver 4 wireless card the driver from Linksys does not work with ndiswrapper.  Use the inprocomm .inf driver and it will work.  It took me forever to figure this out.

---

