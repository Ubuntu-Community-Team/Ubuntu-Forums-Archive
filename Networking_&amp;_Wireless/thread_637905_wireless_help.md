---
title: "wireless help"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by zakee on 2007-12-11
I have a BCM 4311, and i can connect to my router, and put in the WPA for it. But when i do i don't get a ip address from it. My other computer running XP can get a ip address from it fine. Can anyone help me?

---

### Post by kevdog on 2007-12-11
What driver are you using, and have you install wpa supplicant?

---

### Post by digitalbenji on 2007-12-11
What type of wireless router do you have?  Are you certain it is in fact a router?

---

### Post by zakee on 2007-12-11
no i have not installed a wpa supplicant, Linksys. mybe it's my DHCP Client.
And my work has a DHPC server running. but i'm connected to te access point.
But have no clue on why i'm not geting a ip address. My Windows computer is geting one from the same access point

---

### Post by kevdog on 2007-12-11
Please post

lshw -C network
iwlist scan

---

### Post by zakee on 2007-12-11
Sorry i restarted my computer like 3 times now it's working. Thanks for helping me guys.

---

### Post by nosh276 on 2007-12-11
Hey, I didn't want to start a new thread. I'm still having wireless trouble after going through countless posts that say they should work.

I'm on an HP laptop with a Linksys WPC54g v2 wireless card. My router is a Netgear WGR614 v6.  I've tried using the ndiswrapper, reinstalling the drivers, and other things which I can't remember and couldn't adequately describe even if I could. I'm running the latest release of Ubuntu (gutsy) 7.10.


I ran   lshw -C network
>   *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a5:d7:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.2 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:b3:3f:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+



iwlist scan
> *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a5:d7:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.2 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:b3:3f:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
mcleod@mcleod:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:41:D1:08
                    ESSID:"McLeod"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/100  Signal level=29/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 1

lspci
> sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:41:D1:08
                    ESSID:"McLeod"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/100  Signal level=29/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

mcleod@mcleod:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


Any help will be greatly appreciated.

---

### Post by nosh276 on 2007-12-11
bump

---

### Post by kevdog on 2007-12-11
Ok, everything you posted looks good.  What isnt working.

---

### Post by nosh276 on 2007-12-12
It just won't connect to the wireless internet at all. I starts trying to connect, but it can never communicate with the router, I guess. It works fine when I boot up windows.:(

---

### Post by kevdog on 2007-12-12
It sounds like you are trying to use network manager.

Here is what I would suggest.  I would try to debug your connection by attempting to connect from the command line to an unencrypted connection. The instructions are in my signature.  You can add WEP or WPA to the mix once you get the unencrypted connection up and going.

---

### Post by nosh276 on 2007-12-12
You are a godsend. Thank you so much. This has been driving me crazy for days.

---

