---
title: "Broadcom BCM94311MCG 8.04, not working"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by virgilnilson on 2008-04-20
I followed the instructions in Invaleed's post for ndiswrapper as well as a few other threads before that, zero errors with Invaleed but still no blue light.

Help =[

---

### Post by minus198 on 2008-04-26
I'd want help with this too..

---

### Post by Jamie Jackson on 2008-04-27
Both of you: Post the output of ```
lshw -C network
```

---

### Post by Boort on 2008-04-27
Jamie Jackson,

Hello, I'm also having this problem with a Lenovo 3000 N100. It was running no problems with the NDIS drivers under ubuntu v7.10 after following your steps from November ([http://ubuntuforums.org/showpost.php?p=3767216&postcount=273](http://ubuntuforums.org/showpost.php?p=3767216&postcount=273)) Today I updated from 7.10 to hardy and found the wireless no longer working. Here is the output you requested from the earlier posters:
lshw -C network:
```

  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d4:d7:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.115 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

and the output of lspci|grep Net:
```
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

I have followed the steps that I found at 
[http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/](http://linuxsalatiga.wordpress.com/2008/04/24/bcm43xx-ndiswrapper-in-hardy/)

I now have bcm43xx, b43, and B44 blacklisted in /etc/modprobe.d/blacklist. I have removed and reinstalled the Windows drivers (same ones that I was using) both from the GUI and command line. also /etc/rc.local now contains the following commands:
```
   rmmod ssb
   rmmod ndiswrapper
   modprobe ndiswrapper
   modprobe ssb
```
These were added because someone found that unloading and reloading the modules fixed their problem. When I tried it form the command line I got the interface up but could not log on to my wireless network.

Thank you in advance for any help you can provide!

---

### Post by microwaver on 2008-04-27
I've got an other problem. 
When I do the lshw -C network i get this 
```

*-network UNCLAIMED
description: Network controller
product : BCM4310
vendor: Broadcom Coporation
physical id: 0
bus info : pci@0000:05:00.0
version: 01
width: 64 bits
clock 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency: 0

```
and the rest is of my ethernet connector

I'm useing a Dell Vostro 1000

any idea on how to enable this card?

---

### Post by Jamie Jackson on 2008-04-27
> **microwaver said:**
> I've got an other problem. 
When I do the lshw -C network i get this 
```

*-network UNCLAIMED
description: Network controller
product : BCM4310
vendor: Broadcom Coporation
physical id: 0
bus info : pci@0000:05:00.0
version: 01
width: 64 bits
clock 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency: 0

```
and the rest is of my ethernet connector

I'm useing a Dell Vostro 1000

any idea on how to enable this card?

Have you tried [this]("http://ubuntuforums.org/showthread.php?t=475963")?

---

### Post by Jamie Jackson on 2008-04-27
> **Boort said:**
> Jamie Jackson,

Hello, I'm also having this problem with a Lenovo 3000 N100.

Try this:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
ndiswrapper -l
lshw -C network

```

...and reply with the output of the last two commands.

---

### Post by minus198 on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Solved everything since someone added those last "rmmod" lines!

---

### Post by Jamie Jackson on 2008-04-27
> **minus198 said:**
> [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Solved everything since someone added those last "rmmod" lines!

Which rmmod lines are you referring to when you say 'those last "rmmod" lines?'

Had you tried a series of rmmod/modprobe lines before without success, and then an updated series fixed the problem?  (I maintain that wiki and forum thread, and I'm trying to collect all the facts.)

---

### Post by SpectralDesign on 2008-04-27
Not working for me..... Here is the requested info:

user@Presario-V6000:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
user@Presario-V6000:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
user@Presario-V6000:~$ sudo rmmod ssb
user@Presario-V6000:~$ sudo rmmod ndiswrapper
user@Presario-V6000:~$ sudo modprobe ndiswrapper
user@Presario-V6000:~$ sudo modprobe ssb
user@Presario-V6000:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
user@Presario-V6000:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:5b:30:f6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:4b:9a:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=72.140.99.253 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
user@Presario-V6000:~$

---

### Post by kevdog on 2008-04-27
So things are working for you now with that configuration?

---

### Post by SpectralDesign on 2008-04-27
> **kevdog said:**
> So things are working for you now with that configuration?
No, not working...

I also tried this:

[http://ubuntuforums.org/showthread.php?t=760568]("http://ubuntuforums.org/showthread.php?t=760568")

I'm also trying WICD and network-manager, neither one works with either howto...

---

### Post by SpectralDesign on 2008-04-27
> **kevdog said:**
> So things are working for you now with that configuration?
...and then I noticed your sig...

so checking the link about CL troubleshooting I was able to get this:
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

to work, or so it seems... Thanks, I'll keep testing and see if I can get it going with encryption!

---

### Post by kevdog on 2008-04-27
Id recommend the command line at first -- just for troubleshooting purposes.  Once things work, you can default back to NM or WICD, or just keep with the command line.

---

### Post by Boort on 2008-04-28
> **Jamie Jackson said:**
> Try this:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
ndiswrapper -l
lshw -C network

```

...and reply with the output of the last two commands.

Jamie,
   OK I received errors on the rmmod b43 and b44 (likely because I have them blacklisted in /etc/modprobe.d/blacklist) SSB and ndiswrapper unloaded and reloaded successfully. 
   Here is the output of the "ndiswrapper -l" command:
```

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

```

   Here is the output of the "lshw -C network" command:
```

  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:5b:51:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

``` 
I did not include the info for the eth0 wired interface since it was unchanged from what I posted above.

   It now appears that I have a eth1 interface and can see my access point. I still have not been able to connect to the network due to not having wicd after the update. (I was not able to get wifi-radar to ever use the WPA supplicant successfully under 7.10) 

I'm going to install WiCD and will let you know how it goes.
THANK you for your help getting the interface up!

Regards,
BoorT

---

### Post by taipoh on 2008-04-28
Just installed 8.04 on my Dell D630, wireless card is Dell 1490 (BCM94311 or BCM94312).  Running into weird issues.

Since b43 is in the 2.6.24 kernel now, I updated the firmware per [these instructions]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") (when I booted up before updating the firmware a message showed up in dmesg saying I had the wrong firmware version).

Now, my wireless card can see broadcasting networks (iwlist), but can't connect to them (via command line or the graphical tool).  It can't even connect to unencrypted ones.

lshw -C network outputs my wireless card as wlan0, but there's no driver=XX where there should be one.

So, I'm assuming it's a driver issue.

Also, I get error messages in /var/syslog I think along the lines of "cannot change wlan0 state."

---

### Post by harshaambati on 2008-04-28
i am having problem with my wirless i am using Hp Pavilion da2432nr

I am a new user i have ubuntu 8.04 after installing ubunt udetected my wireless installed b43-fwcutter which inturn has installed ndiswrapper-utlis-1.9, i also have given location the .inf file (.i.e. bcmwl6.inf) of my driver
but nothing happens wireless connection is not shown in network manager...

these are some details of my wirless card...

 #lspci -v | less

01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1374
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at b3000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

I also tried these rmmod command but no result
# rmmod b43
ERROR: Module b43 does not exist in /proc/modules
# rmmod b44
ERROR: Module b44 does not exist in /proc/modules
# rmmod ssb
# rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
# modprobe ndiswrapper
root@sriharsha-laptop:/home/sriharsha# modprobe ssb
root@sriharsha-laptop:/home/sriharsha# ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
root@sriharsha-laptop:/home/sriharsha# lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

can any one help me ..with this...problem..

---

### Post by kevdog on 2008-04-29
Can use the bcmwl6 driver -- this has been discussed in numerous threads -- this is a Vista driver.  You need bcmwl5 or the WinXP driver.

---

### Post by Jamie Jackson on 2008-04-29
> **kevdog said:**
> Can use the bcmwl6 driver -- this has been discussed in numerous threads -- this is a Vista driver.  You need bcmwl5 or the WinXP driver.

kevdog meant "can't" use the bcmwl6 driver. The bcmwl6 is almost guaranteed to fail for current versions of ndiswrapper.

---

### Post by uschxc on 2008-04-29
useless post, didn't finish the tutorial

---

### Post by Boort on 2008-04-30
> **Jamie Jackson said:**
> Try this:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
ndiswrapper -l
lshw -C network

```

...and reply with the output of the last two commands.

Jamie,

Running 
   ```

   sudo rmmod ssb
   sudo rmmod ndiswrapper
   sudo modprobe ndiswrapper
   sudo modprobe ssb
   
```
appear to give me a working eth1 device when run from the command line. After running them I have been able to login to an unprotected wireless network. My current situation is that I can use the wireless interface as long as I open a command line and stop and restart ndiswrapper and ssb (B43 and B44 are no longer loading since they are blacklisted)
   They do not seem to run from /etc/rc.local on startup. Any ideas why this is?
   I have removed wifi-radar and replaced it with WiCD but have not yet tried to connect to my WPA2 access point. I hope to have time to try tomorrow evening.
Here is the output of "ndiswrapper -l"
```

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

```

Here is the output of "lshw -C network"
```

  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:5b:51:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

Thank you for your assistance!
BoorT

---

### Post by BlueFeast on 2008-04-30
```
*-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:73:05:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

thats what i get....please help

---

### Post by Jamie Jackson on 2008-04-30
> **BlueFeast said:**
> ```
*-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:73:05:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

thats what i get....please help

That's theoretically good output, though. What are the symptoms of your current problem?

---

### Post by jw5801 on 2008-05-01
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

:D

---

### Post by Spainface on 2008-05-01
I'm having the same problem. For some reason I can't get the module to change from ssb to ndiswrapper.  I tried all the "5 minute" solutions etc. 

lshw -C network gives me this:

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb



and this is in my /etc/rc.local

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

Any thoughts?

Thanks!

---

### Post by jw5801 on 2008-05-02
> **Spainface said:**
> I'm having the same problem. For some reason I can't get the module to change from ssb to ndiswrapper.  I tried all the "5 minute" solutions etc. 

lshw -C network gives me this:

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb



and this is in my /etc/rc.local

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

Any thoughts?

Thanks!

```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
```
Then reboot.

Or if you want it now:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
```

You'll need the first one as well though, if you want it to stick aftera reboot.

---

### Post by tashmooclam on 2008-05-02
I had a Broadcom card in a Dell laptop. I struggled and thought I was making mistakes. I changed to WICD. Finally, I went on ebay and bought an Intel wireless card for $25. Problem solved! The Linux drivers for Intel cards are in the Ubuntu OS. This was by far the best $25 I ever spent.

---

### Post by Spainface on 2008-05-02
Great, thanks!  My trouble was that I had tried so many different ways that each new one was just using the settings from the last, so I wiped everything clean and it worked.

Thanks again,

---

