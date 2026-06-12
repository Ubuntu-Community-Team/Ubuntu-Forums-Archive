---
title: "Can not connect wired or wireless - Broadcom Corporation NetXtreme BCM5751"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by user440 on 2008-08-13
Pulled from [This thread]("http://ubuntuforums.org/showthread.php?t=888664") where I hijacked the topic a bit (unintentionally of course).

System is a Dell D410 laptop with Kubuntu 8.04


> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US B UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US B UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US B2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC H6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethe rnet PCI Express (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802. 11g Wireless LAN Controller (rev 02)


> 
I executed that above, but I do not see anything of value in the output (probably not saying much):

To be clear, neither wired nor wireless is working on this particular LT.

Thanks again Jim!


Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
lshw -version

-version print program version (B.02.12.01)

format can be
-html output hardware tree as HTML
-xml output hardware tree as XML
-short output hardware paths
-businfo output bus information

options can be
-class CLASS only show a certain class of hardware
-C CLASS same as '-class CLASS'
-disable TEST disable a test (like pci, isapnp, cpuid, etc. )
-enable TEST enable a test (like pci, isapnp, cpuid, etc. )
-quiet don't display status
-sanitize sanitize output (remove sensitive information like serial numbers, etc.)


Thanks again for the help!

---

### Post by user440 on 2008-08-13
And here's the output with the correct command executed:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Proces
sor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Exp
ress Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Gr
aphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                                                              B2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (IC                                                              H6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem                                                               Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev                                                               03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                                                               Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethe                                                              rnet PCI Express (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.                                                              11g Wireless LAN Controller (rev 02)
user440@LT-D410:~$ lshw -C
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

user440@LT-D410:~$ sudo lshw -C network
[sudo] password for user440:
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:6c:d1:f1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:88:bc:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

**EDIT:**  I know it says 'disabled' above.  For the wired (eth0) is shows enabled in the system settings.  If one goes into the configuration menu, either automatic or manual dhcp or bootp can be selected.  If auto - dhcp is selected, it disables the card.  

If I try to enable the wireless, a 'changing interface' dialog pops up for a split-second, then it goes back to showing 'disabled wireless device'.

Thanks again!

---

### Post by chili555 on 2008-08-13
Mike-

It looks like your wired ethernet connection is all ready to go. Please hook up an ethernet cable and do:```
sudo dhclient eth0
```Does it connect or sleep?

---

### Post by user440 on 2008-08-13
> **chili555 said:**
> Mike-

It looks like your wired ethernet connection is all ready to go. Please hook up an ethernet cable and do:```
sudo dhclient eth0
```Does it connect or sleep?

&@#$&#@&$@#@#$&!!!!!  <slaps head>  I executed the command you provided while plugged in, the result just was not making sense.  I happen to think, geee, I wonder if the cable could be bad or the router port.... I looked on the back, hey no lights.  Swapped out the high quality cable for one of my others and BINGO - wired access!

1 down - Thanks!

**EDIT:** I decided to post the output anyway.  Uhhh, does this make sense?

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
etho: ERROR while getting interface flags: No such device
etho: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device

---

### Post by user440 on 2008-08-13
Wireless works!

Damn I love this OS!  Did the updates, identified I needed the driver patch, downloaded and rebooted, whola!  

Thank you very much for your help!

Best,

Mike

---

### Post by Ayuthia on 2008-08-13
> **user440 said:**
> &@#$&#@&$@#@#$&!!!!!  <slaps head>  I executed the command you provided while plugged in, the result just was not making sense.  I happen to think, geee, I wonder if the cable could be bad or the router port.... I looked on the back, hey no lights.  Swapped out the high quality cable for one of my others and BINGO - wired access!

1 down - Thanks!

**EDIT:** I decided to post the output anyway.  Uhhh, does this make sense?

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
etho: ERROR while getting interface flags: No such device
etho: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device

It looks like your wired card is working.  That is your eth0 card.  The reason why the command did not work for you is because you used the letter O instead of the number zero (0).  

For your wireless, you have an option to try using the b43 driver by installing b43-fwcutter.  You can do this through Synaptic or if you want, you can do it through the Terminal:
```
sudo apt-get install b43-fwcutter
```

Once it installs, I think that they recommend that you restart your computer.

I am not for sure about how well the b43 driver works with your card though.  I have seen mixed results.

---

### Post by user440 on 2008-08-13
Once I did the updates, the wireless worked like clock work.  Thanks!

---

