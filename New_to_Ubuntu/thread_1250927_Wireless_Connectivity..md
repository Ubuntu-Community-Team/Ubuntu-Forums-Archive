---
title: "Wireless Connectivity."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by skyring on 2009-08-27
Just as a starter, I am very impressed with Ubuntu, I am a linux beginner and decided to start my journey at ubuntu. I've read a couple of books/articles and had a quick flick through the desktop and the system control menus but I've really had no time get stuck in and have a real play on the OS, but on the surface its a thumbs up!
 
One thing I noticed when using the 9.10 alpha (had it on a disk with a magazine) was that I couldn't connect to my wireless network correctly (from a desktop machine). Is this is a problem with the alpha or my hardware? The books/articles that I read said it was simple to connect to wirless via the network manager, but I couldnt get connected as described. I'm at work at the moment, I've got a 9.04 distro sat on my desk waiting to be installed. Is the wireless connectivity working in 9.04? and is there any driver to install or command to run to get it working? Its a belkin PCI card.
 
Just looked up what a stupidly long post for a shortish question. 
 
Thanks for your help.

---

### Post by nothingspecial on 2009-08-27
You need to post your wireless card.

Open up a terminal (in accessories in the menu)

Type ```
sudo lshw -C network
```

and copy the output here.

---

### Post by mapes12 on 2009-08-27
> Its a belkin PCI card.Hello skyring and welcome to the Ubu forum.

Wifi is generally well supported in Ubu, particularly with the newer version which you have. However, some hardware vendors still keep their driver code to themselves which means it's difficult for a developer to write the code for the linux kernel to support the wifi adapter. The good news is there are many fixes when this happens.

If you could go Applications>Accessories>Terminal then type ```
sudo lspci
```press enter. Copy and paste the output back here then someone can have a look at your card in a bit more detail to locate a fix.

BTW - the problem is usually not faulty hardware.

EDIT - Alpha is a pre release testing version of Ubu. 9.04 is the current stable version. If you're new to Ubu then perhaps 9.04 would be a smoother Ubu experience.

---

### Post by bkratz on 2009-08-27
> **skyring said:**
> Just as a starter, I am very impressed with Ubuntu, I am a linux beginner and decided to start my journey at ubuntu. I've read a couple of books/articles and had a quick flick through the desktop and the system control menus but I've really had no time get stuck in and have a real play on the OS, but on the surface its a thumbs up!
 
 
Thanks for your help.


9.10 alpha is just that;  an alpha (before beta and before RC (release candidate) and before the released version)  and unexpected errors may (will)  occur.  Being a first time user of Ubuntu you probably should stick with the 9.04 release until comfortable. 9.04 is very stable and well supported.  IF you like and stay with Ubuntu it is easily upgraded to 9.10 in October when released.

Here is a link to the Belkin cards natively supported.  Other options like Ndiswrapper are available if yours is not listed.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

---

### Post by skyring on 2009-08-27
Thanks, will boot in and try those commands, I guessed the alpha may have been the issue, so I switched to 9.04. Will report back asap.

---

### Post by skyring on 2009-08-27
> sudo lshw -c networkReturned this:
```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:a1:20:77
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:3b:52:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:4a:84:da:86:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```annnnnd
> 
sudo lspcireturned:
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:a1:20:77
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:3b:52:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:4a:84:da:86:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by bkratz on 2009-08-27
Use the search link above for BCM4306--a lot of people have covered this well.  Here is a good place to start.


[http://ubuntuforums.org/showthread.php?t=1168538&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1168538&highlight=BCM4306)

---

### Post by skyring on 2009-08-28
Oh man! I didnt know there was that much crap floating around, if I'd have known I wouldn't have posted >.< 
 
I'm at work again today, so once I get home I'm gonna try a few things.
 
Just checking does [this]("http://ubuntuforums.org/showthread.php?t=1182333&highlight=BCM4306") look like it will fix my issue?
 
Edit - also will [this](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) remedy the issue?

---

### Post by skyring on 2009-08-29
Thanks for the info, my wireless works better under linux than it does under windows! it was a combination of the links in my above post that fixed it. I installed the ndiswrapper packages then followed the guide in the other link!

Im so happy with my ubuntu build now! :D now time to play!!!!! :D :D :D

---

### Post by viper3500 on 2009-08-29
Hi,
I have just installed ubuntu on my computer and have run in to a problem. on ubuntu it doesnt recognize my adapter at all so i am unable to get on the internet at all. the model of my adapter is f5d8055. plz help
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7868280") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7868280")

---

### Post by 3rdalbum on 2009-08-29
> **viper3500 said:**
> Hi,
I have just installed ubuntu on my computer and have run in to a problem. on ubuntu it doesnt recognize my adapter at all so i am unable to get on the internet at all. the model of my adapter is f5d8055. plz help

Please read the posts by "nothingspecial" and "mapes12".

---

