---
title: "Wireless network adapter dissapeared..."
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by morganGDFP on 2007-02-08
I have a big problem.
Yesterday I was sitting in front of my relatively freshly installed ubuntu 6.10 and everything was working perfectly well. 

I switched my computer off, went to bed and switched it on again this morning. 

To my surprise my wireless network adapter no longer existed.
I looked in administration->networking and it is no longer visible there.
And of course I cannot connect to the internet either..

Looking in the device manager I see the device but I don't understand what I can do with it and how to get it back and running again.

Now I'm using WinXP on the same computer and here everything works fine.

I'm using a D-Link AirPlus DWL-G520 Wireless PCI adapter.

Someone help please.

---

### Post by a5benwillis on 2007-02-08
I have had this happen to me after installing something that modified my restricted modules. In my case I believe that it was during my Twinview setup and NVIDI Adriver install.

You can try running: sudo apt-get install linux-restricted-modules-generic

It will likely find a conflict with another version. If you choose 'y' and install then your wirelesswill show up again.


HTH

---

### Post by morganGDFP on 2007-02-08
Now i really need some serious help here.
I was playing around with my relatively freshly installed ubuntu 6.10 yesterdar and was very happy that everything was working.
I switched off my comp, went to bed and this morning I started it up again.
To my surprise my wireless network was nowhere to be found..

If I go into administration -> networking I can see "Wired connection" and "Modem connection" but absolutely non sign of "Wireless connection". 
I cannot comprehend how this has happened and desperately need help.
Now i am using winXP on the same computer and here it is no problems at all.

My network card is: D-Link Airplus DWL-G520 Wireless PCI Adapter(rev.B) 
(From winXPs Device Manager)

I have now read and done the first step in the WifiDocs/WirelessTroubleShootingGuide.
I get this output from running lshw:

  *-network:0 
description: Ethernet interface  
product: SiS900 PCI Fast Ethernet        
vendor: Silicon Integrated Systems [SiS] 
physical id: 4        
bus info: pci@00:04.0         
logical name: eth0        
version: 91        
serial: 00:11:d8:73:cf:41        
size: 10MB/s        
capacity: 100MB/s        
width: 32 bits        
clock: 33MHz        
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation        
configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=half link=no multicast=yes port=MII speed=10MB/s        
resources: ioport:8800-88ff iomemory:d5000000-d5000fff irq:201   

*-network:1 UNCLAIMED        
description: Ethernet controller        
product: AR5212 802.11abg NIC        
vendor: Atheros Communications, Inc.        
physical id: a        
bus info: pci@00:0a.0        
version: 01        
width: 32 bits        
clock: 33MHz        
capabilities: bus_master cap_list        
resources: iomemory:d4800000-d480ffff irq:10 

root@morgan-desktop:~#  

It would appear that ubuntu finds the network adapter but does not run any driver for it..

I guess i could go to MADWIFI, download a driver for the G520 and install it but just to make sure I don't cause any more damage 
I want to make sure there is no other step which I should try first..

Cheers

---

### Post by ukripper on 2007-02-09
before doing that,  first try running following:

$ sudo depmod -a
$ sudo modprobe ndiswrapper

Then:
$ sudo ifdown eth1  
$ sudo ifup eth1

or 

$ sudo ifdown wlan0
$ sudo ifup wlan0


check if it appears in network manager and then enable it.:)

---

### Post by morganGDFP on 2007-02-10
No that did not work..
here is the output:

morgan@morgan-desktop:~$ sudo depmod -a
morgan@morgan-desktop:~$ sudo modprobe ndiswrapper
morgan@morgan-desktop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
morgan@morgan-desktop:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

My wireless network was named ath0 before.
I tried those ifup and ifdown commands for ath0 but I get a similar output.

It does not appear in the network manager.

What would be the next step?

---

### Post by shane634 on 2007-02-10
Give us the output of this command from a terminal:

```
lspci
```

  This should give us the chipset which may help.

---

### Post by lojic on 2007-02-10
Does the following command:

uname -a

show that your using the 2.6.17-11 kernel?  If so, you may want to post your wireless hardware info here:

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

---

### Post by morganGDFP on 2007-02-11
> Does the following command:

uname -a

show that your using the 2.6.17-11 kernel? If so, you may want to post your wireless hardware info here:



```
uname -a
Linux morgan-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

```

No it appears as if i'm still using the 2.6.17-10-generic kernel..Does this mean I can look forward to loosing my wireless one more time when I upgrade?..Assuming we can fix it this time. :)

The output from lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
**00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)**
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

```

When reading the other forums posts about this kind of problem I got the impression the one of those Atheros cards (that I seem to be having) was the way to go in ubuntu..

I went in and had a look in /lib/modules/2.6.17-10-generic/kernel/drivers/net/
and found no .ko files that I could associate with my wireless card..But then again, I have no idea what they should look like :lolflag: 

By this time I have also tried to install the drivers from MADWIFI but that did not work either.
I just tried do a **make** and then **modprobe ath_pci** but i got the reply that module ath_pci was no found.

It was working flawless before..Is there no way of, say, putting in the LiveCD and restore only the drivers to the way they were before?

(It is getting really frustrating to boot into winXP every time I need the internet)

---

### Post by WorldPax on 2007-02-11
I am having the same problem on my wife&#347; computer. I had the same problem with the initial install but selecting the multiverse and restricted packages fixed it, and it has been running fine until the update. I think the problem might be in those packages but I have no idea how to fix that.

BTW Atheros AR5212 chipset.

---

### Post by morganGDFP on 2007-02-11
yes I think that's what I should do..install those damn restricted packages..
sudo apt-get install linux restricted$(uname -r) (or something like that)

By reading the other posts that seems to solve the problem for most people..

There is a small problem with that though..
I'm running a stationary computer and the router is upstairs and I have no cable long enough to connect to it.. I can't move the router either..And I really don't want to unplug all those cables from under the desk and move my computer up there..

I can access internet on WinXp on the same computer.
Is there any way I can download those restricted-package-things, save them on my external HD, and then do the apt-get thing offline?

Cheers

---

### Post by morganGDFP on 2007-02-15
I got it.
went and bought a 15 m ethernet cable, installed the linux restricted stuff, the network manager, restarted and then it was up and running again.
Thanks everyone for the help

---

### Post by ubuntu_demon on 2007-02-22
> **morganGDFP said:**
> I got it.
went and bought a 15 m ethernet cable, installed the linux restricted stuff, the network manager, restarted and then it was up and running again.
Thanks everyone for the help

congrats :)

This is even better. First find out which kernel you have :
$uname -r

Then choose which one to install based on that result :
$ sudo aptitude install linux-generic
$ sudo aptitude install linux-386
$ sudo aptitude install linux-686

This packes makes sure that you will always have the relevant restricted modules even after a kernel upgrade.

morganGDFP please don't double post. I've merged both threads.

---

