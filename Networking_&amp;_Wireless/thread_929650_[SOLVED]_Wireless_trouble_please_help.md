---
title: "[SOLVED] Wireless trouble please help"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by notanerd on 2008-09-25
Hello I have just converted to ubuntu 8.04 lts

I can't turn on my wireless card

i typed "sudo lshw -C network" into Terminal and this comes up

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:80:44
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.3 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:7c:4d:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

can someone please tell me in step by step form what i need to enable the wireless card. Thank you

---

### Post by caljohnsmith on 2008-09-25
It looks like you can probably use one of either the b43 or b43legacy modules depending on what your BCM4306 chipset revision is. From the official [b43/b43legacy wireless driver website]("http://linuxwireless.org/en/users/Drivers/b43"), it says the BMC4306 chipset is supported for:
> bcm4306 (Rev. 2 uses b43legacy, Rev. 3 uses b43) 

So I think the next step would be to figure out what revision you have, and your lshw output didn't say anything about revision. You might try:
```
lspci -v
```
Look for your wireless card chipset BCM4306 in that output and see if it gives any info on revision; I suspect that lspci won't tell us any more about revision then lshw, but it's at least worth a try. If that doesn't give revision info, do you have any documentation for your wireless card that says? 

Anyway, a good guide to help you use those modules is:

[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Let me know how it goes, or if you have questions I'll be happy to try and help. I know it can be daunting at first get wireless working in Linux, but it isn't usually too big a deal for most cards. If the above methods don't work, we can also try with ndiswrapper, but I would try the above first.

---

### Post by notanerd on 2008-09-26
Ok so it no longer says the network is disabled, but the wireless still doesn't auto detect networks. when i type in 

sudo lshw -C network into terminal now this comes up

 *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:80:44
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.3 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:7c:4d:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Does ubuntu wireless ever autodetect networks or do you have to type in all the details?

---

### Post by willca on 2008-09-26
Try this out in a terminal.

sudo iwlist wlan0 scan

If this detects wireless networks in the area then the driver is loading right.

Next thing to figure out is how you intend to connect to a hotspot, if you use encryption or not.

Sometimes, if there is no encryption involved, the built-in Network Manager work well. Otherwise I just edit my config files and do it via CLI.

---

### Post by notanerd on 2008-09-26
it comes up with "no scan results"

---

### Post by tariquepark on 2008-09-26
try typing into a command line
ifup wlan0

and see what the output is
if there is nothing then all is good

---

### Post by notanerd on 2008-09-26
It came up with this

Ignoring unknown interface wlan0=wlan0

---

### Post by notanerd on 2008-10-03
still can't get it working

---

### Post by Ayuthia on 2008-10-03
You might try the bcm43xx module.  It seems to give some better results for people with your card.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=935259](http://ubuntuforums.org/showthread.php?t=935259)

---

### Post by notanerd on 2008-10-04
Ok i am totally stuck, nothing seems to be working for me. Is there a chance i am overloading the system with different firmware or anything like that?

---

### Post by notanerd on 2008-10-05
I am going to kill myself soon

---

### Post by kforum on 2008-10-05
did you try the given link, without success?

---

### Post by notanerd on 2008-10-05
I have tried all methods on this thread and many others with no success.

---

### Post by Idefix82 on 2008-10-05
Please post the output of
```
lspci
```
here.

---

### Post by notanerd on 2008-10-05
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by Bucky Ball on 2008-10-05
System->Admin->Network

Unlock and click on wireless then check the properties. Make sure 'Configuration' is set to 'Automatic DHCP' and 'Enable Roaming' is unticked. Make sure your router is serving DHCP. Any luck?

---

### Post by notanerd on 2008-10-05
how do i know if the router is DCHP, also I don't know the different between WEP and WPA when it is talking about passwords

---

### Post by Bucky Ball on 2008-10-05
> **notanerd said:**
> how do i know if the router is DCHP, also I don't know the different between WEP and WPA when it is talking about passwords

Let's presume the router is serving DHCP and you are using no security, as if you were you would know your user name and security details for the router/LAN.

Follow the previous instructions and see what happens. :)

---

### Post by notanerd on 2008-10-05
I know the network name and the password is 8 digits long, but i dont know whether to select wep or wpa, or any variations of them

---

### Post by Bucky Ball on 2008-10-05
Try wep then wpa. One of them is right.

---

### Post by kforum on 2008-10-05
i would assume its wep 128 key(not ascii, if its numbers).

it seems to me like this si your mistake, since you CAN input that info, your prob just not configuring it right. please check with whoever set your net up and ask them about the related info, is it dhcp(auto asigned IPs) or is it static ip, what iind of sicurity lock you got, etc...

you NEED to know these things lad...

good luck,

cheers.

---

### Post by Bucky Ball on 2008-10-05
> **kforum said:**
> 
you NEED to know these things lad...



Could be a lassie ... :)

---

### Post by notanerd on 2008-10-05
could be a lad and a lassie :)

Ok so it turns the network is not secured, and i can get a connection but it stays at 0% and won't let me load any pages. My housemate is connected right now with Vista. I have another question too, does ubuntu ever auto detect networks in the area or do you have know the details to connect to it?

---

### Post by notanerd on 2008-10-16
The problem seems to be that the computer doesn't detect any networks? There are 5 networks within range. Network Manager doesnt detect it and i just installed wicd and it doesnt detect anything either? Suggestions?

---

