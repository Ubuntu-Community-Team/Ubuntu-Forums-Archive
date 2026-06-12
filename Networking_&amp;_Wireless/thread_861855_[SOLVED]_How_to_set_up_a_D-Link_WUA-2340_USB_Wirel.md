---
title: "[SOLVED] How to set up a D-Link WUA-2340 USB Wireless Adapter"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by jkyahoo101 on 2008-07-17
I am very new to Linux and would like to know how to set up my wireless adapter. The make and model are in the thread title. I have installed Ubuntu 8.04 on the pc. Thanks for any help.

---

### Post by jkyahoo101 on 2008-07-17
Sorry for bumping but I really need help on this. I need it done by tomorrow sometime.

---

### Post by jkyahoo101 on 2008-07-17
Does anyone know?

---

### Post by auxis on 2008-07-17
One solution (dirty, but will most likely work) is using ndiswrapper.  Installation guide: [http://ubuntuforums.org/showthread.php?t=574501&highlight=wg311v2](http://ubuntuforums.org/showthread.php?t=574501&highlight=wg311v2)

And the drivers located here: [ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip](ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip)

You might be able to get it working.

I hope this helps.

---

### Post by jkyahoo101 on 2008-07-17
That does not help at all. It is way too confusing. Like I said I am very new to Linux. Isn't there some built in feature that will allow me to install the drivers for my adapter?

---

### Post by auxis on 2008-07-17
Open up a terminal by going to Applications -> Accessories -> Terminal.  Type the following:

```

sudo iwlist wlan0 scan
```

Tell me what the output of that is.

---

### Post by jkyahoo101 on 2008-07-17
It says interface doesn't support scanning.

Edit: I just had an idea. Would it be possible for some kind person to set up the drivers and then send them to me? My dad wants it connected to the internet before tomorrow otherwise he is going to switch back to XP.

---

### Post by adam_kimber on 2008-07-17
Hmmm. What does (Applications -> Accessories -> Terminal) typing ```
ifconfig
``` give you?

From research the post by auxis is pretty much right. Unfortunately you will have to use ndiswrapper to use this card. However once done you should be able to use it no probs. Check out this if that post was confusing [http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html]("http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html")

However if you walk through either step by step you will be able to do it. From both posts you will have to do the majority of the work in the terminal. Copy and paste is your friend :P

Just shout if you need anything explaining.....

PS Have you tried going to here? System --> Administration --> Hardware Drivers ?? That has my wireless card in it. All I had to do was enter my password, click the checkbox and reboot. Hope this works....

---

### Post by jkyahoo101 on 2008-07-17
It says this.(picture) Ok I will try the second one but I am very new to Linux. Any way to send the files or something?

When I get to sudo ndiswrapper -m it says [sudo] ndiswrapper command not found.
Now what?

---

### Post by adam_kimber on 2008-07-17
According to the screenshot you have no network cards installed! :P Try the PS first. LO or loopback is an internal LInux/Unix system. It can be used for all sorts of applications..... Ask if you want to know more.

---

### Post by jkyahoo101 on 2008-07-17
> **adam_kimber said:**
> According to the screenshot you have no network cards installed! :P Try the PS first. LO or loopback is an internal LInux/Unix system. It can be used for all sorts of applications..... Ask if you want to know more.

That is my problem I need to get my D-Link WUA-2340 USB Wireless Adapter installed for it to work. I have no idea what you said on the second part.

---

### Post by adam_kimber on 2008-07-17
Lol. Don't worry about it. Did you try looking at the Hardware Drivers section first?

System --> Administration --> Hardware Drivers

If there is nothing there then we will ahve to try the ndiswrapper thing. (Just out of interest what does typing lsusb get you (in a terminal)

---

### Post by jkyahoo101 on 2008-07-17
There is nothing in it and says no drivers are installed.

lsusb: 
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 07d1:3a08 D-Link System
Bus 001 Device 001: ID 0000:0000

---

### Post by auxis on 2008-07-17
Unfortunately, getting your drivers to work will require a bit of reading.  Using this guide [http://ubuntuforums.org/showthread.php?t=574501&highlight=wg311v2](http://ubuntuforums.org/showthread.php?t=574501&highlight=wg311v2) will get you through installing ndiswrapper.

ndiswrapper download: [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=602481](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=602481)

Your Drivers: [ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip](ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip)

When you have ndiswrapper installed, the specific files that the guide will talk about will be located in (assuming you extracted your files to your desktop) /home/yourname/Desktop/20071112-WUA-2340-S0026/Drivers/WinXP_2K

---

### Post by jkyahoo101 on 2008-07-17
Thanks. I already have my drivers but I didn't have the ndiswrapper stuff. I noticed that the guide and the download are different versions. Will that make a difference?

---

### Post by adam_kimber on 2008-07-17
It was an off chance. Ubuntu is starting to get common drivers for these things in its repo. 

First make sure ndiswrapper is installed. Now this is going to be a faff as I reckon you are using a different computer to access the internet to the one with the Ubuntu installation on it. Am I right? Just click on the i386 or amd64 or all links in the download section and save them. Then copy them to the other machine. Double click them to install. 

Get the following debs (installers for Ubuntu) from here. 
[Ndiswrapper common]("http://packages.ubuntu.com/hardy/ndiswrapper-common")
[ndiswarpperutils]("http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9")

Download the drivers from [here]("ftp://ftp.dlink.com/Wireless/wua2340/Drivers/WUA2340_driver_140.zip")

Then follow the instructions on that page i linked to. OR use auxis pages. Both appear to work. Beauty of Linux. Many ways to do stuff. :P

(FYI Ndiswrapper is clever program that enables Linux/Ubuntu to use windows drivers for wireless hardware.)

---

### Post by auxis on 2008-07-17
> **jkyahoo101 said:**
> Thanks. I already have my drivers but I didn't have the ndiswrapper stuff. I noticed that the guide and the download are different versions. Will that make a difference?

No, it shouldn't have an effect. Simply replace the version he's referring to (1.48 ) with 1.53.

Edit:  After reading adams previous post, his method seems like it would be a lot more easier to do.  But if it doesn't work, you can always fall back to the one I gave.

---

### Post by jkyahoo101 on 2008-07-17
Yes I am using my XP install which is on the internet. I am using a jump drive to transfer files like that picture earlier. Now how do I know what one to click on i386 or amd64?

---

### Post by adam_kimber on 2008-07-17
jkyahoo101 the link auxis gave you is technically correct. However most of the time when you see programs that are contained within a tar.gz (compressed file like a zip) they require compiling, which whilst most of the time is not too hard is a process I don't think you wish to get involved in...... (yet)

If in doubt get both and install the i386 one. If that fails I can tell you how to uninstall and then install the other. If you installed Ubuntu yourself you would have probably downloaded the i386 version and therefore you need to use that, 

> **dave9191 said:**
> If you type 

uname -m

into a console it will tell you the version of the kernel. And for a 32 bit machine you would see something like ix86. Im guessing that for the 64 bit you would see something like x86-64 or AMD64 or EM64T. 

You should install the right one for your processor. So dont install the 64 bit one if you have a 32 bit machine. 

Dave

---

### Post by jkyahoo101 on 2008-07-17
So what do I have to do step by step? All I want is my adapter to work. I could do this in XP in 5 min but in Linux I am totally confused.

---

### Post by adam_kimber on 2008-07-17
Right.

1) Download debs and drivers. (Just like in XP - software downloads)
2) Copy to Ubuntu machine. Place on desktop as its easy to find.
3) Double click debs to install.
4) Right click on zip and go to extract (you should now have either a) a folder or b) a bunch of files plastered across the desktop. Leave them for now we can tidy that up later....
5) Open terminal Accessories --> terminal (just copy and paste the bits after the dash and space and paste into the terminal (use mouse right click copy and paste)
6) Type the following into the terminal - sudo depmod -a
7) Type the following into the terminal - sudo modprobe ndiswrapper
8) Type the following into the terminal - sudo ndiswrapper -m
9) Type the following into the terminal - sudo lsmod | grep ndiswrapper
10) The result of the above makes sure that the program is working. The output should have a couple of lines with ndiswrapper in it.

11) Install drivers. This is done by the following.
12) Type the following into the terminal - cd ~/Desktop 
13) Note the name of the extracted folder from step 4
14) Type the following into the terminal - cd <name from step 13>
15) cd Drivers
16) cd WinXP_2K
17) sudo ndiswrapper -i netA5AGU.inf
18) Driver is now installed
19) Test using sudo ndiswrapper -l - should list your driver
20) Reboot

If you have further problems just shout. (Look at the pages linked to)

XP / Vista have their own share of problems. Wireless and printing are Linux's problem children

---

### Post by jkyahoo101 on 2008-07-17
Ok that seems simple enough except I don't know what you mean by debs. When you said download debs.

What is debs?

---

### Post by adam_kimber on 2008-07-17
> **adam_kimber said:**
> 
Get the following debs (installers for Ubuntu) from here. 
[Ndiswrapper common]("http://packages.ubuntu.com/hardy/ndiswrapper-common")
[ndiswarpperutils]("http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9")


Debs are installers for Ubuntu (they have the extension .deb hence the name :)). Nothing more. For an in depth wikipedia article check [this]("http://en.wikipedia.org/wiki/Deb_(file_format)") out. Though you probably don't want to read that yet. (V technical)

WOO 100 posts :D

---

### Post by jkyahoo101 on 2008-07-17
Ok. But how do I know to chose i386 or amd64? And is it hard to install them? And which one do I install first?

---

### Post by adam_kimber on 2008-07-17
Type the following into a terminal uname -m 

If it states i686 or i386 then use the i386 ones. I would use the i386 one anyway as unless you knowing installed a 64bit version of Ubuntu then you use be running a 32bit (or i386/i686) 

Debs are easy to install. Just double click them, and click install. You will need to enter your password as usual with installing programs. 

ndiswrapper-common first then the utils

---

### Post by jkyahoo101 on 2008-07-17
O if its a case of 32bit and 64bit I know I installed a 32bit version. I am going to start installing stuff then.

---

### Post by jkyahoo101 on 2008-07-17
Well I guess this is good since it said driver installed when I did that last line of code. Now I am rebooting. What is the next step?

---

### Post by adam_kimber on 2008-07-18
Try the following. 

* Open System->Administration->Network
* You should see your wireless connection in the list, click the Unlock button to make changes.
* Select your wireless connection and hit the properties button.
* Deselect 'Roaming'
* Select your wireless network from the list and enter in your WPA/WEP information for the card.
* Click ok, and now you have a working wireless connection. Congrats!

---

### Post by adam_kimber on 2008-07-18
If you are still having problems you could try this. Its supposed to work out-of-the-box.

[http://ubuntuforums.org/showthread.php?t=863155]("http://ubuntuforums.org/showthread.php?t=863155")

---

### Post by jkyahoo101 on 2008-07-18
There is no wireless option in the network connections.

---

### Post by tvcasualty on 2008-10-28
I gave this my best crack, drivers are said to be installed, but light will not come on, on the dongle.  (Light activates when devices is active).  No option for selecting the card.  Simply would not work.:(

---

### Post by jimjutte on 2008-11-27
I'm getting as far as step 17, where I am supposed to install the .inf file... and I get bad command (or something like that). Why would this be? Should I have removed other drivers that might have been installed for another adapter? I had a different adapter but for some reason, after a year it, just up and died.

Any thoughts on resolving the issue?

---

### Post by Colinchocolate on 2010-01-14
When I try this, it says it can't find cd~/Desktop

---

### Post by bkratz on 2010-01-14
> **Colinchocolate said:**
> When I try this, it says it can't find cd~/Desktop

did you leave a space between cd  and ~?

---

### Post by Colinchocolate on 2010-01-14
yes. I just messed up typing it here.
:)

---

### Post by bkratz on 2010-01-14
I just did that step only and mine says

brian@brian-desktop:~/Desktop$ 

So I am at the desktop!

I guess I will read the rest and see

---

### Post by Colinchocolate on 2010-01-14
OK, I have the driver installed, but i can't find the Network button, under Administration.
I have set up my home network under Wireless connection, but nothing happens. I've entered the WEP key too. Is my driver installed wrong? It worked when I tested it through ndiswrapper.

---

### Post by Colinchocolate on 2010-01-14
In case it is needed, im running an ubuntu 9.10.

---

### Post by bkratz on 2010-01-14
Can you copy/paste the output of

sudo lshw -C network
(that is LSHW in lowercase)
here.


-you might as well do 

sudo iwlist scan

also

---

### Post by Colinchocolate on 2010-01-14
one sec....

---

### Post by Colinchocolate on 2010-01-14
sudo lshw -C network =
*-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VM (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 81
       serial: 00:0b:cd:2e:f2:63
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:f0400000-f0400fff ioport:1000(size=64)
sudo iwlist scan =

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by bkratz on 2010-01-15
> **Colinchocolate said:**
> sudo lshw -C network =
*-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VM (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 81
       serial: 00:0b:cd:2e:f2:63
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:f0400000-f0400fff ioport:1000(size=64)
sudo iwlist scan =

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




As you can see from the above the system is not even "seeing" the card. This is what a typical ndiswrapper output should look like:

```

  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 00:01:80:65:aa:69
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:31:d8:36:e4:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:11:f3:3b:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.53+Marvell,11/27/2006,1.0.4.9 ip=192.168.1.66 link=yes multicast=yes wireless=IEEE 802.11g



```


As you can see there is a entry for wireless interface (mine is wlan0) showing ndiswrapper as the driver.


Try ( in the terminal) lsusb (that is LSUSB in lowercase) and see if it even is detected.  First, is there some type of switch or pushbutton to turn the wireless on/off?  Secondly, you might want to check the bios and see if it can be turned on/off there. After that if no joy I would check out this help file.

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by Colinchocolate on 2010-01-15
[LIST=1]
[*] Card: D-Link WUA-2340(USB)
 
[LIST]
[*] Chipset: Unknown (Atheros?)
[*] usbid: 07d1:3a07
[*] Driver: Driver available on accompanying CD and on [www.dlink.com]("http://www.dlink.com/"). Installed on WinXP machine to get access to drivers in windows/inf folder, and program files/D-Link folder. (I added both oem47.inf, athfmwdl.sys, ar5523.bin, and oem48.inf, a5agu.sys, ar5523.bin) EDIT: Worked only when: Used with ndiswrapper version 1.30; Used D-link driver version 101 with NetA5AGU.inf, this .inf file is the only driver file needed.
[*] Other: Able to recognize hardware (ndiswrapper -l showed hardware pressent) using same procedure as for the DWL-1340, but on loading the kernal module, wlan0 appeared but was not configurable and did not respond to ifdown/ifup, so I couldn’t get this device to work with ndiswrapper. EDIT: This device was able to work with ndiswapper version 1.30 and NetA5AGU.inf from D-link website
[*] Success: Though others above have had success with ndiswrapper version 1.30, I was unable to compile this old version against my kernel sources (2.6.22-suspend2-r2) due to a change in some kernel macro specs. Later versions of ndiswrapper would compile, install drivers, modprobe properly, but... nothing happened. No dmesg errors, but no dmesg output about loading drivers either, even though ndiswrapper -l showed the drivers there, and the hardware present. This has been fixed in ndiswrapper 1.49, which works perfectly with the neta5agu.inf driver (version 1.20). The wlan0 interface is initialized on my laptop, and by issuing a “ln -s /etc/init.d/net.lo /etc/init.d/net.wlan” followed by a “/etc/init.d/net.wlan start” my already-installed wpa_supplicant sprang into action and connected me to my WPA-PSK protected router. Can’t ask for more.
[/LIST]
[/LIST]
**Found this about my chip, what should I do?**

---

### Post by bkratz on 2010-01-15
> **Colinchocolate said:**
> [LIST=1]
[*] Card: D-Link WUA-2340(USB)
 
[LIST]
[*] Chipset: Unknown (Atheros?)
[*] usbid: 07d1:3a07
[*] Driver: Driver available on accompanying CD and on [www.dlink.com]("http://www.dlink.com/"). Installed on WinXP machine to get access to drivers in windows/inf folder, and program files/D-Link folder. (I added both oem47.inf, athfmwdl.sys, ar5523.bin, and oem48.inf, a5agu.sys, ar5523.bin) EDIT: Worked only when: Used with ndiswrapper version 1.30; Used D-link driver version 101 with NetA5AGU.inf, this .inf file is the only driver file needed.
[*] Other: Able to recognize hardware (ndiswrapper -l showed hardware pressent) using same procedure as for the DWL-1340, but on loading the kernal module, wlan0 appeared but was not configurable and did not respond to ifdown/ifup, so I couldn’t get this device to work with ndiswrapper. EDIT: This device was able to work with ndiswapper version 1.30 and NetA5AGU.inf from D-link website
[*] Success: Though others above have had success with ndiswrapper version 1.30, I was unable to compile this old version against my kernel sources (2.6.22-suspend2-r2) due to a change in some kernel macro specs. Later versions of ndiswrapper would compile, install drivers, modprobe properly, but... nothing happened. No dmesg errors, but no dmesg output about loading drivers either, even though ndiswrapper -l showed the drivers there, and the hardware present. This has been fixed in ndiswrapper 1.49, which works perfectly with the neta5agu.inf driver (version 1.20). The wlan0 interface is initialized on my laptop, and by issuing a “ln -s /etc/init.d/net.lo /etc/init.d/net.wlan” followed by a “/etc/init.d/net.wlan start” my already-installed wpa_supplicant sprang into action and connected me to my WPA-PSK protected router. Can’t ask for more.
[/LIST]
[/LIST]
**Found this about my chip, what should I do?**

What is this? did you ever do the lsusb?  did it find the card?

---

### Post by Colinchocolate on 2010-01-15
The previous post was from the ndiswrapper site.

I forgot to record the lsusb results, one sec...

[http://ubuntuforums.org/showthread.php?t=885847&page=68](http://ubuntuforums.org/showthread.php?t=885847&page=68)

that's where i posted most of my results from the troubleshooting guide

---

### Post by Colinchocolate on 2010-01-15
lsusb=
Bus 002 Device 002: ID 045e:009d Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 001 Device 002: ID 0bc2:2101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

when I run Windows Wireless Network Drivers (presumably ndiswrapper)
it says "Unable to see if Hardware is Present", then opens and says
neta5agu
Hardware present: Yes

---

### Post by Colinchocolate on 2010-01-15
hello?

---

### Post by bkratz on 2010-01-15
I just went through the whole thread. Did you get your ndiswrapper files like it said in post #16?  If so, they are version 1.5 files. The current version of ndiswrapper is 1.55.  I don't know and perhaps you might ask Pytheas22 in your other posting if that makes a difference with compatibility of the current kernel. He is the best with ndiswrapper and would know the answer. Still looking

---

### Post by bkratz on 2010-01-15
By the way, I would suggest you do not use encryption on the wireless AP until this all is sorted out.

---

### Post by Colinchocolate on 2010-01-15
Ok

---

### Post by ekennes on 2010-01-25
Same Problem as Coli chocolate

---

### Post by ekennes on 2010-01-26
Tried Again it works now seems important that you have all driver files you download in the the directory with the .inf file:D

---

### Post by Twmaster on 2011-01-02
Ok, I am stuck. I'm trying to get one of these D-Link wireless dongles working.

I've installed ndiswrapper from the software center, installed the drivers from the CD that came with the adapter. 

A probe of the USB bus shows the device. ndiswrapper reports the card present and drivers installed. I do not have a wlan0 dev shown in /etc/dev and of course it does not show up in the network tool.

I've read all the entries here in the forums and the wiki. I'm out of ideas.

Thanks in advance.

---

### Post by Twmaster on 2011-01-02
More info. I used the WinXP driver. After grepping the dmesg I find it complaining about a 64 bit kernel and the driver not being 64 bit. 

I tried the Vista64 driver with yet another spectacular failure...

```
wmaster@Penguin:~$ dmesg | grep -e ndis -e wlan
[   14.354589] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.452948] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   16.452958] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   16.452964] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   16.452991] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   16.452999] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   16.453013] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   16.453020] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   16.453028] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   16.453035] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   16.453042] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   16.453049] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   16.453064] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   16.453075] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   16.453082] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   16.453089] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   16.453098] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   16.453105] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   16.453135] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   16.453145] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   16.453157] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   16.453164] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   16.453172] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   16.453179] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   16.453186] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   16.453193] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   16.453200] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   16.453207] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   16.453214] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   16.453222] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   16.453229] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   16.453236] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   16.453243] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   16.453250] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   16.453257] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   16.453264] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   16.453275] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   16.453281] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   16.453284] ndiswrapper (load_sys_files:206): couldn't prepare driver 'agux64'
[   16.453834] ndiswrapper (load_wrap_driver:108): couldn't load driver agux64; check system log for messages from 'loadndisdriver'
[   16.453887] usbcore: registered new interface driver ndiswrapper

```

*sigh* It's late. Time for bed.

---

### Post by caseydk on 2011-01-06
***Exact*** same issue here. Really frustrating as I bought this card an hour ago. :(

---

### Post by Relinies on 2012-06-14
We've all got the same problem, even as far as Ubuntu 12.04. The adapter just DOES NOT start working. It can be detected, it can be installed, but it just DOES NOT begin flashing/detecting networks.
So, how can we solve this?

---

### Post by Rubi1200 on 2012-06-14
Thread closed

Reason: necromancy

Thanks to all for participating.

---

