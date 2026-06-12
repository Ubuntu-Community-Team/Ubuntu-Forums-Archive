---
title: "Broadcom Corporation BCM4318 (Wireless) driver??"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Liambiscuit on 2008-08-06
I recently installed Ubuntu linux on my Gateway PC, but the PC can pick up the wireless card but not show any access points. I ran "Hardware Testing" and learned that the card is a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" I have tried to use ndiswrapper but I struck no gold. If someone can tell me how to use Ndiswrapper or a good alternative, The help would be greatly appreciated. (The computer has internet access now, but I don't want to carry the tower up 2 flights of stairs every time I want to download somthing xD.

Thanks in advance,
Simitra.

EDIT: BTW I am running 8.10 Hardy Heron.

---

### Post by pytheas22 on 2008-08-06
I think that b43 (the driver being used by default for your card) may not support your particular chipset well.  bcm43xx (an older driver) should work better, from what I gather from Google.  Therefore ndiswrapper shouldn't be necessary (it would probably still work, but it would be preferable to have bcm43xx).  Try following these steps to get the card working under bcm43xx (I'm assuming that you can plug into a wired connection for these steps; if that's impossible, please let me know):

1. blacklist b43 driver and ndiswrapper:

```
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'ndiswrapper' >> /etc/modprobe.d/blacklist
```

2. install bcm43xx firmware:
```

sudo apt-get install bcm43xx-fwcutter
```

You should be prompted to download and install the firmware automatically when you run this command.  Say yes.

3. reboot and you should have working wireless.  If it still won't work, please open up a terminal (Applications>Accessories menu), run these commands, and post the output here:
```

iwlist scan
lshw -C Network
lspci -nn
```

---

### Post by soan on 2008-08-07
Tried this to fix my problem but did not seem to work.Here is the output as requested:

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690 [Radeon X1200 Series] [1002:791e]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
03:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
03:07.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev c0)

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:77:9e:29
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.0.0.34 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

Any help would be much appreciated.

---

### Post by superm1 on 2008-08-07
You may consider trying the experimental broadcom driver... [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by pytheas22 on 2008-08-07
> You may consider trying the experimental broadcom driver... [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

This may work too; I don't know what the status of the latest b43 code is, but if it purports to support all Broadcom chipsets, then it would probably work for you (is there any way to find out for sure if this code will support BCM4318 reliably?).

Otherwise, soan, it looks like the driver that you installed yesterday (bcm43xx) is not driving your card for some reason because it's being pushed out by b43.  Please try running this code and post the output:
```

sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
iwlist eth1 scan
```

It should manually force the removal of the competing modules, and make your wireless work.

---

### Post by superm1 on 2008-08-07
> **pytheas22 said:**
> This may work too; I don't know what the status of the latest b43 code is, but if it purports to support all Broadcom chipsets, then it would probably work for you (is there any way to find out for sure if this code will support BCM4318 reliably?).

Otherwise, soan, it looks like the driver that you installed yesterday (bcm43xx) is not driving your card for some reason because it's being pushed out by b43.  Please try running this code and post the output:
```

sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
iwlist eth1 scan
```It should manually force the removal of the competing modules, and make your wireless work.
This actually isn't based on the b43 driver.  It's a driver produced by Broadcom.

---

### Post by pytheas22 on 2008-08-07
> This actually isn't based on the b43 driver. It's a driver produced by Broadcom.

Wait, I'm confused.  I thought Broadcom hated Linux and that's why the bcm43xx/b43 project has spent so long reverse-engineering drivers through a Chinese wall.  And you say that Broadcom has released a Linux driver?  Is the source open and if so is it under the GPL or what?  I hadn't heard anything about this; if you could provide a link to more information, I'd appreciate it.

Also, you say in your guide, "This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready. It should support all of the Broadcom A/B/G adapters and some of the Broadcom N adapters."  Do you mean Intrepid, not Hardy?  I thought the Ubuntu policy was not to push out updates other than security and major bug fixes once a version of Ubuntu has been released?

If I can get more information on what the deal is with this driver from Broadcom, I might try it for my bcm4306 card, but I'm very confused now because I hadn't heard anything about this.

---

### Post by superm1 on 2008-08-07
> **pytheas22 said:**
> Wait, I'm confused.  I thought Broadcom hated Linux and that's why the bcm43xx/b43 project has spent so long reverse-engineering drivers through a Chinese wall.  And you say that Broadcom has released a Linux driver?  Is the source open and if so is it under the GPL or what?  I hadn't heard anything about this; if you could provide a link to more information, I'd appreciate it.

Yes it is a broadcom released driver: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
It's not very open yet, but they are working on making it more open, and working with the right people to do so.  It's living in LRM until it's more open.

> 
Also, you say in your guide, "This driver is being introduced in hardy, but the GUI to enable it in Jockey is not yet ready. It should support all of the Broadcom A/B/G adapters and some of the Broadcom N adapters."  Do you mean Intrepid, not Hardy?  I thought the Ubuntu policy was not to push out updates other than security and major bug fixes once a version of Ubuntu has been released?

Actually it went out the door at Hardy launch but only supported 2 of the newer cards  that were critical for a Dell platform..  This revision of it supports more cards.

> 
If I can get more information on what the deal is with this driver from Broadcom, I might try it for my bcm4306 card, but I'm very confused now because I hadn't heard anything about this.
Yeah it hasn't been very vocalized as of yet.  Now that more cards are supported, this is why I'm trying to get some more feedback on it.

---

### Post by superm1 on 2008-08-07
Well I should mention, the 4318 that this thread is about actually isn't advertised as "supported", but it's possible that it does work.  The driver is advertised to support 4311, 4312, 4321, and 4322

---

### Post by pytheas22 on 2008-08-07
Wow, very interesting.  Do you have any idea why Broadcom finally decided to release this?  I knew they had Linux drivers all along, since something needs to be driving the Broadcom chips in wireless routers that run Linux, but my sense had always been that Broadcom was extremely uncooperative with the Linux community and refused to release any kind of drivers publicly.  I hope they didn't decide to release these drivers now just to screw over the bcm43xx/b43 people who have spent so long tediously reverse-engineering stuff, by negating all of their efforts.

Also, is there any reason why we should want to use Broadcom's drivers instead of those of the b43 project?  After all, b43 is pretty close to supporting every chipset with the basic features, and I think that advanced stuff is supposed to be on the way.  I'd think that until Broadcom releases the full source of its drivers, b43 would be preferable.  I understand why we should at least test Broadcom's drivers to see how well they work, but is there anything you can say about projected future plans, at least on Ubuntu?  Are we going to abandon b43 in favor of Broadcom's driver, and if so are we going to make sure that Broadcom makes the drivers free?

When I get a chance I'll see about using Broadcom's driver on my bcm4306 chip and let you know if it works (I know they don't say anything about supporting 4306).

---

### Post by superm1 on 2008-08-07
> **pytheas22 said:**
> Wow, very interesting.  Do you have any idea why Broadcom finally decided to release this?  I knew they had Linux drivers all along, since something needs to be driving the Broadcom chips in wireless routers that run Linux, but my sense had always been that Broadcom was extremely uncooperative with the Linux community and refused to release any kind of drivers publicly.  I hope they didn't decide to release these drivers now just to screw over the bcm43xx/b43 people who have spent so long tediously reverse-engineering stuff, by negating all of their efforts.

This has been a request from Dell for them to get a driver to support the Broadcom cards in Dell laptops as they are much less expensive than the Intel cards generally.  The intention is a functional monolithic driver now and gradually opening it up over time.

It's not just to "screw over" the b43 people, but Broadcom is one of those companies that takes some time to work well with open source.  If you go back a few years a similar scenario happened with the tg3 driver and their closed driver.  It's now open and when bugs pop up every so often Broadcom does pop in and help out.  

> 
Also, is there any reason why we should want to use Broadcom's drivers instead of those of the b43 project?  After all, b43 is pretty close to supporting every chipset with the basic features, and I think that advanced stuff is supposed to be on the way.  I'd think that until Broadcom releases the full source of its drivers, b43 would be preferable.  

Yes and no.  For some people functionality is more important than a fully open driver.  Take a look at how many people use the closed source nvidia drivers.  

First yes:

[LIST]
[*]This driver is legally sound.  Extracting firmware from a driver hosted on a website that doesn't actually have the rights to redistribute the driver is quite a gray area.
[*]Also, this driver supports a handful of adapters that aren't yet in b43.  
It also has some better performance than the b43 drivers from what i've seen.  Once you get it up and running, you'll see that scans are very snappy and it can do large transfers without losses in speed.
[*]This driver doesn't need the internet to install.  Once it's properly in the archive and not proposed, and shows up on some CDs, you will be able to do installs without needing to grab firmware from somewhere
[/LIST]

Now no:

[LIST]
[*]It's hard to go on a company's word that they will open a driver up and play nice, especially Broadcom.  Using their closed driver doesn't help the situation.
[*]Using this driver may slow the efforts of the reverse engineering on the b43 driver with less eyes on it.  You can look at the flip side still that this driver can help the reverse engineering since you can actually look at it's operations on a Linux system too.
[/LIST]
> 
I understand why we should at least test Broadcom's drivers to see how well they work, but is there anything you can say about projected future plans, at least on Ubuntu?

The current plan is to keep this driver in the archive, but to still offer B43.  So when you get the restricted drivers popup, you will have both options and be able to choose and swtich between the two with a reboot.

> 
 Are we going to abandon b43 in favor of Broadcom's driver, and if so are we going to make sure that Broadcom makes the drivers free?

No as indicated above, they will both be offered.  Dell and Canonical are both driving efforts to ensure that Broadcom is opening their drivers.  With the quantity of Ubuntu systems being shipped outside the US to places like China, Dell does have the ability to speak with the dollar and will be doing so.

> 
When I get a chance I'll see about using Broadcom's driver on my bcm4306 chip and let you know if it works (I know they don't say anything about supporting 4306).
Hopefully some luck with the 4306 :)

---

### Post by Cenotaph on 2008-08-11
Just thought i should mention that with my bcm4318, i'm experiencing the best results with the latest b43 driver (that's present in kernel 2.6.25 and 2.6.26). the b43 in 2.6.24 suffers from the same small range issue that bcm43xx did, and ndiswrapper is not playing well with network manager in my rig for some reason.

To install it in hardy you should get compat-wireless-2.6 from [http://www.linuxwireless.org](http://www.linuxwireless.org) and follow the instructions. The firmware for this driver is also different from the one hardy's b43-fwcutter package in ubuntu downloads, so if anyone wants to try it be sure to check b43's page in linuxwireless for firmware installation.

compat-wireless will be included in the linux-backports-modules from the next kernel version in hardy, it's already in hardy-proposed repository actually, but until it's fully tested i recommend using the source from linuxwireless.org

i haven't tried the broadcom driver still cause im happy with this solution, but it's nice to see broadcom finally releasing some drivers for their cards. I guess that after a lot of time with driver woes for this card, we will get two good options in intrepid. quite ironic.

---

### Post by alex_mayorga on 2008-11-16
> **superm1 said:**
> Well I should mention, the 4318 that this thread is about actually isn't advertised as "supported", but it's possible that it does work.  The driver is advertised to support 4311, 4312, 4321, and 4322

Unfortunately I have this card on a Inspiron 1501:
```
$ lspci -vvnn
...
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Device [1028:0007]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl
...
$ uname -a
Linux inspiron-1501 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

```

Yet on 8.10 I'm not being offered the STA driver but only the B43 driver, that unfortunately won't work at all (it associates just fine using WEP but it's not possible to ping the default gateway when unwired)

What do I do to have jockey offer me STA?

FWIW, here's also my bug report on this [https://bugs.edge.launchpad.net/bugs/286071](https://bugs.edge.launchpad.net/bugs/286071)

Thanks in advance

---

### Post by pytheas22 on 2008-11-16
alex_mayorga: from what I understand (although superm1 would be able to tell you better), the module for the STA driver is called 'wl' and should be built into the Intrepid kernel.  You should be able to activate it by typing:
```

sudo modprobe -r b43 b44 ssb bcm43xx
sudo modprobe wl
```

I don't think it requires any firmware, although I could be wrong--again, superm1 or someone else who has actually used the STA driver would be able to give you better information.

Also, you could always use ndiswrapper to drive this card if neither b43 nor wl will work; read [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for easy instructions.

---

### Post by alex_mayorga on 2008-11-23
> **pytheas22 said:**
> 
Also, you could always use ndiswrapper to drive this card if neither b43 nor wl will work; read [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for easy instructions.

'wl' didn't work reliably for me, but ndiswrapper did the trick, thanks a bunch.

---

### Post by WitchCraft on 2010-12-05
Driver installation is always the same.


Graphics:
NVIDIA and ATI graphics card GL driver you needn't install, because they don't work anyway.
Else see wireless:

Wireless:
Download and install the latest kernel
Then search for the firmware, if necessary.

For Broadcom B43:
apt-get install firmware-b43-installer

For SuSe:
zypper install b43-fwcutter
/usr/bsin/install bcm43xx_firmware
zypper install fw

Sound:
Is in the kernel. Update the kernel, and problems are gone.
But when you update the kernel, you may need to recompile ALSA.
If there's no sound as root, you need to start the pulseaudio-daemon.
(/usr/bin/pulseaudio)

---

### Post by ichase on 2010-12-20
Greetings,
I have been reading about this broadcom issue to the point my head hurts. In the b43 page: [b43]("http://www.linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian") it states to type: ```
sudo apt-get install b43-fwcutter
``` then says > You will be asked to automatically fetch and install the firmware into the right location.
All I get is, that b43-fwcutter is installed but does not asked to automatically fetch and install the firmware. I did this via ethernet with a good internet connection.
Now this is the part I do not understand. When I load Parted Magic Live CD, which loads itself into RAM, It recognized my WiFi and took a whopping 10 minutes to set up my WiFi. Parted Magic is based on an independent distro. So how can it so easily recognize the wife card. BCM4318 but a major distro can't?
There is probably an easy explanation for this and being a very new Linux user I do not know what it is. 
 
All the best,
 
Ian

---

### Post by guntu on 2010-12-20
> **Liambiscuit said:**
> I recently installed Ubuntu linux on my Gateway PC, but the PC can pick up the wireless card but not show any access points. I ran "Hardware Testing" and learned that the card is a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" I have tried to use ndiswrapper but I struck no gold. If someone can tell me how to use Ndiswrapper or a good alternative, The help would be greatly appreciated. (The computer has internet access now, but I don't want to carry the tower up 2 flights of stairs every time I want to download somthing xD.

Thanks in advance,
Simitra.

EDIT: BTW I am running 8.10 Hardy Heron.


A very common problem - I've had it once and again and see people have it all the time - yet the solutions is rather simple! 

Try this  [http://ubuntuforums.org/showthread.php?p=9903527](http://ubuntuforums.org/showthread.php?p=9903527)

If you still have any problems, let us know.. 

Godd luck

---

### Post by bkratz on 2010-12-20
> **guntu said:**
> A very common problem - I've had it once and again and see people have it all the time - yet the solutions is rather simple! 

Try this  [http://ubuntuforums.org/showthread.php?p=9903527](http://ubuntuforums.org/showthread.php?p=9903527)

If you still have any problems, let us know.. 

Godd luck




You do realize this was posted almost 2-1/2 years ago, right?

---

### Post by pytheas22 on 2010-12-20
> **ichase said:**
> Greetings,
I have been reading about this broadcom issue to the point my head hurts. In the b43 page: [b43]("http://www.linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian") it states to type: ```
sudo apt-get install b43-fwcutter
``` then says 
All I get is, that b43-fwcutter is installed but does not asked to automatically fetch and install the firmware. I did this via ethernet with a good internet connection.
Now this is the part I do not understand. When I load Parted Magic Live CD, which loads itself into RAM, It recognized my WiFi and took a whopping 10 minutes to set up my WiFi. Parted Magic is based on an independent distro. So how can it so easily recognize the wife card. BCM4318 but a major distro can't?
There is probably an easy explanation for this and being a very new Linux user I do not know what it is. 
 
All the best,
 
Ian

As bkratz points out, this thread is quite old, and the b43-fwcutter probably doesn't work the way it used to (I no longer use a laptop with a Broadcom chip so I'm not sure).

It's hard to say why the wireless is not working for you without more information, however.  It's possible the firmware is not installed (it would be under the /lib/firmware/b43 directory if it is), that b43 does not support your card and you need to use the Broadcom STA driver instead, or that there's some other problem.  If you post the output of these commands we can probably help:
```

ls /lib/firmware
dmesg | grep -e b43 -e wlan -ie firmware
lshw -C Network
lspci -nn | grep -i broadcom
sudo iwlist scan
```

As for why your wireless card works in Parted Magic but not Ubuntu, it's probably because Parted Magic ships with the b43 firmware pre-installed.  Ubuntu doesn't do this because there are some legal ambiguities regarding its right to redistribute the firmware.  Parted Magic likely has less to worry about on the legal front than do Ubuntu and Canonical.

---

### Post by Brittanie Marie on 2011-11-02
So I am also new to using linux and I have spent the last 2 hour using google and the forums on here to try and get my wireless to work. After plugged into a wired connection I was still not able to get internet however it changed my wireless from being disabled and not allowing me to enable it to "Device not ready (firmware missing). 

my wireless card is a Broadcome Corporation BCM4318 [AirForce One 54g] 802.06.02.0 Network controller [14e4:4318] (rev 02) 

I guess I am just trying to figure out a way to fix or download the drives for the firmware so my wireless does work though without using internet. I have one computer that does have internet and a USB flash drive I can use to transfer files. Though will this work and if so what should I download to fix it. 

The laptop I am using is a compaq presario v5000.

I would greatly appreciate any ones help on this! 

Brittanie

---

### Post by wildmanne39 on 2011-11-02
Hi welcome to the forum! this should work check out post 3 at this link.
[http://ubuntuforums.org/showthread.php?t=1873690](http://ubuntuforums.org/showthread.php?t=1873690)
Thank you

---

### Post by pytheas22 on 2011-11-03
**Brittanie Marie**: please follow wildmanne39's link for getting the firmware in place.  We can also probably get your wired Internet working if you post the output of the commands "lspci -nn" and "lshw -C Network"; if the wireless is all you care about, though, maybe the wired isn't important.

---

### Post by Brittanie Marie on 2011-11-03
> **wildmanne39 said:**
> Hi welcome to the forum! this should work check out post 3 at this link.
[http://ubuntuforums.org/showthread.php?t=1873690](http://ubuntuforums.org/showthread.php?t=1873690)
Thank you

Hey Thank you. I followed the post to the T though I am still not able to access wireless. I posted below the results from terminal. If you have any suggestions that I could you I would appreciate it greatly. 

  	 	 	 	 	 	  brittanie@Brittanie-Marie:~$ sudo mkdir /lib/firmware/b43  
 [sudo] password for brittanie:  
 mkdir: cannot create directory `/lib/firmware/b43': File exists  
 brittanie@Brittanie-Marie:~$ cp Desktop/b43/* /lib/firmware/b43  
 cp: cannot create regular file `/lib/firmware/b43/a0g0bsinitvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g0bsinitvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g0initvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g0initvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1bsinitvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1bsinitvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1bsinitvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1initvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1initvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/a0g1initvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0bsinitvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0bsinitvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0bsinitvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0initvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0initvals5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/b0g0initvals9.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0bsinitvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0bsinitvals14.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0bsinitvals15.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0initvals13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0initvals14.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/lp0initvals15.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/n0absinitvals11.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/n0bsinitvals11.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/n0initvals11.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/pcm5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode11.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode13.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode14.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode15.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode5.fw': Permission denied  
 cp: cannot create regular file `/lib/firmware/b43/ucode9.fw': Permission denied  
 brittanie@Brittanie-Marie:~$ sudo rmmod -f b43  
 brittanie@Brittanie-Marie:~$ sudo rmmod -f ssb  
 brittanie@Brittanie-Marie:~$ sudo modprobe b43

---

### Post by wildmanne39 on 2011-11-03
Hi, after you enter the first command you will need to enter your user password, it will not show the password on the screen so when you are done typing it hit enter.
Run the commands one line at a time.
Thank you

---

### Post by pytheas22 on 2011-11-03
> Hi, after you enter the first command you will need to enter your user password, it will not show the password on the screen so when you are done typing it hit enter.
Run the commands one line at a time.
Thank you

It looks like the problem was not actually with entering the password; that was done correctly.  It didn't work because the "sudo" was missing from the second command: it should have been:
```

sudo cp Desktop/b43/* /lib/firmware/b43
```

and not just:
```

cp Desktop/b43/* /lib/firmware/b43
```

---

### Post by dFlyer on 2011-11-03
From the directory you downloaded your firmware file you need to:

sudo cp Desktop/b43/* /lib/firmware/b43

This will require you to put in your password.

---

### Post by wildmanne39 on 2011-11-03
Hi pytheas22, thank you I missed that I was helping to many people at the same time earlier.

---

### Post by Brittanie Marie on 2011-11-03
Thank you everyone. It worked. YAY!!

---

### Post by wildmanne39 on 2011-11-03
Hi Brittanie Marie, your welcome! I am glad it worked.
Enjoy

---

### Post by pytheas22 on 2011-11-03
> Hi pytheas22, thank you I missed that I was helping to many people at the same time earlier.

No problem; I know what that feels like :)

Glad to hear the original issue is solved.

---

### Post by gchild00 on 2011-12-31
Thank you so much. I spent countless hours and 2 sleepless nights trying to find a fix for this and now I found one! I went from forum to forum with all kinds of detailed advice but this by far was the easiest to implement! Thank you so much! I am totally new to linux..loving ubuntu so far though!


> **wildmanne39 said:**
> Hi welcome to the forum! this should work check out post 3 at this link.
[http://ubuntuforums.org/showthread.php?t=1873690](http://ubuntuforums.org/showthread.php?t=1873690)
Thank you

---

### Post by wildmanne39 on 2011-12-31
Hi gchild00, welcome to the forum! I am glad it worked.
Enjoy

---

