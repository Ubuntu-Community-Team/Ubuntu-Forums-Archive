---
title: "[SOLVED] Additional PC can't connect to d-link DI 524 router network"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by adldesigner on 2008-07-11
Hi guys,

I'm writing this on a laptop connected to a network to which I want to add an additional computer. So far I've had no success getting it to work.

Output of commands are the following:

**lspci**
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
**06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)**
```So at least the PCI wireless card is being recognized.

**sudo lshw -C-network**
```
  *-network:0
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 86
       serial: 00:11:95:e0:37:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       **logical name: wlan0**
       version: 20
       serial: 00:19:cb:41:86:33
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g
```So now we know **wlan0** is the interface.

**iwlist wlan0 scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:FB:F3:DC
                    **ESSID:"dlink"**
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1611ms ago
```Found us an ESSID so at least we know it's seeing the network.

**dhclient wlan0**
```
**There is already a pid file /var/run/dhclient.pid with pid 134519120**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:19:cb:41:86:33
Sending on   LPF/wlan0/00:19:cb:41:86:33
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```*"There is already a pid file /var/run/dhclient.pid with pid 134519120"*
[LIST=1]
[*]Does this mean I've got dhclient running in the background?
[*]Do I have to kill it and restart?
[/LIST]

**cat /etc/resolv.conf**
```
nameserver 200.44.32.12
**nameserver 192.168.0.1**
search cantv.net
```According to the instruction manual, *nameserver 192.168.0.1* is supposed to be the router's IP address. Pinging it does nothing.

[LIST]
[*]Network Manager's connection settings for **dlink** is **Automatic configuration (DHCP)**.
[*]Security is a WPA-PSK/WPA2-PSK pass phrase. -By the way, why does the pass phrase change into a really long string?- 
[*]Laptop with working connection runs on Hardy.
[*]Desktop with non-working connection runs on Gutsy.
[/LIST]

I've already seen and tried with many guides, including kevdog's sticky.

**Advice on this situation anyone?**
Thanks for any help! :-k

---

### Post by adldesigner on 2008-07-12
Mi god! Could this be so hard? I've changed settings all around the place, and still there's no way I'm getting DHCPOFFER on **sudo dhclient wlan0**!

I mean, when I **iwlist wlan0 scan** it does see the **dlink** network! How the hell doesn't it get to ping it at least?!

HELP! I've been on it for about 15 hours!
A very frustrated noob. ](*,)

---

### Post by helgman on 2008-07-12
A little bit more information about "the network" might help here. I guess it's wireless since you are trying to configure the wireless interface on your computer.

I'm not really sure about your setup but the fact that the computer "sees" the wireless network doesn't automatically make it connect to it. So more information about how you've tried to connect (via network manager or CLI etcetera).

You need to associate with the network to get an address. If you use the terminal try **sudo iwconfig wlan0 essid dlink** and the try to get a response from the DHCP server on the network. That is if you are not using encryption ...

The [WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) might hold some other useful information if it's a wireless connection you're trying to establish.

Regards,
Helgman

---

### Post by helgman on 2008-07-12
> **adldesigner said:**
> [LIST]
[*]Network Manager's connection settings for **dlink** is **Automatic configuration (DHCP)**.
[*]Security is a WPA-PSK/WPA2-PSK pass phrase. -By the way, why does the pass phrase change into a really long string?- 
[*]Laptop with working connection runs on Hardy.
[*]Desktop with non-working connection runs on Gutsy.
[/LIST]

OK, so I must have skimmed the first post really fast the first time. Sorry about that ...

The WPA-PSK/WPA2-PSK pass phrase turnes into a long string, yes.

I always try to troubleshoot from the terminal since you get a bit more feedback (most of the time).

This is what I would do:
```
wpa_passphrase <essid> <passphrase> > test.conf
sudo wpa_supplicant -i wlan0 -c test.conf
iwconfig wlan0   // to see that the interface associates with the AP
dhclient wlan0   // if it don't get a lease
```
I've also found that static IP might help sometimes when troubleshooting connections.

Regards,
Helgman

---

### Post by adldesigner on 2008-07-12
> **helgman said:**
> 

You need to associate with the network to get an address. If you use the terminal try **sudo iwconfig wlan0 essid dlink** and the try to get a response from the DHCP server on the network. That is if you are not using encryption ...


Hello helgman! Thank you very much for popping by and helping out!

I just woke up, and out of despair, I went to the router and reset the thing. Thought to myself: "heck, maybe I can try and create a new network or something".

Anyway, came back to the connected laptop and tested the connection. Worked fine. Saw your replies, went to the desktop pc, and tried **sudo iwconfig wlan0 essid dlink** and then **dhclient wlan0** and it worked. I'm writing your reply from the desktop which is now connected.

So, Thank You very much for your reply. It helped!
[B]
Questions [/B][LIST=1]
[*]If I rebooted the router to factory settings, does that mean that I've got an unsecured network right now?
[*]I should configure back some encryption right?
[/LIST]

---

### Post by helgman on 2008-07-12
> **adldesigner said:**
> Questions [/B][LIST=1]
[*]If I rebooted the router to factory settings, does that mean that I've got an unsecured network right now?
[*]I should configure back some encryption right?
[/LIST]

I'm not sure what D-Links policies are but my guess is 'yes' on both questions.

Glad you've got the network up and running. I hope applying encryption won't break things for you (it shouldn't).

Regards,
Helgman

---

