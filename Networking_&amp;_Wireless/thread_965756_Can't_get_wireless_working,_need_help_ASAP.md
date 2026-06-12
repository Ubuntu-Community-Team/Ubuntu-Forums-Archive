---
title: "Can't get wireless working, need help ASAP"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Aiex on 2008-10-31
I've been trying to get the wireless connection working on Ubuntu for two weeks, with no success. I finally got the wired connection working, which was nice for getting updates installed, but I really need to get my wireless connection up so I can put the computer in the room it belongs in instead of on the floor. I tried pinging my router, but it says the host cannot be reached. I've tried messing with the network settings, but I don't really know what I'm doing. I have to get this thing fixed before I go back to college *on Sunday *or it'll never get done. Any help you can offer would be appreciated. If you need more info, and I'm sure you will, I'll provide it. Oh, I should mention I installed drivers with ndiswrapper and it said the hardware wasn't present, so I tried a different driver for and it recognized the hardware, but I'm not sure if the chipset is the same and if maybe that's the problem? For the life of me I can't figure this thing out.

---

### Post by helgman on 2008-10-31
Hi!

Have you tried the WifiDocs?

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Check them out and then post back if you don't get it up and running.

Regards,
Helgman

---

### Post by eternal_sage on 2008-10-31
what type of wireless card do you have? if it is a Broadcom, there have been numerous issues lately with these cards.

please run these commands and post up the info returned from them (in the console you can copy by hitting [Shift]+[Control]+[C] and paste with [Shift]+[Control]+[V])

```

sudo lspci -nnm
sudo lshw -C network
sudo iwlist scan

```

---

### Post by Aiex on 2008-10-31
Gave that stuff a second go, but it didn't work any better than the first time. My wireless "card" is a USB stick, so the part there about making sure it's working didn't work. I tried the part about making sure the device is active, but all I got was error messages. Is there anything else you can do for me? I really appreciate the reply by the way.

---

### Post by Aiex on 2008-10-31
sudo lspci -nnm gave me this:
> craig@craig-desktop:~$ sudo lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [2560]" -r01 "Dell [1028]" "Unknown device [0142]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [2561]" -r01 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [24c2]" -r01 "Dell [1028]" "Unknown device [0142]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [24c4]" -r01 "Dell [1028]" "Unknown device [0142]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [24c7]" -r01 "Dell [1028]" "Unknown device [0142]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [24cd]" -r01 -p20 "Dell [1028]" "Unknown device [0142]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 PCI Bridge [244e]" -r81 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [24c0]" -r01 "" ""
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801DB (ICH4) IDE Controller [24cb]" -r01 -p8a "Dell [1028]" "Unknown device [0142]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [24c3]" -r01 "Dell [1028]" "Unknown device [0142]"
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "NV17 [GeForce4 MX 420] [0172]" -ra3 "nVidia Corporation [10de]" "Unknown device [015a]"
02:01.0 "Communication controller [0780]" "Conexant [14f1]" "HSF 56k Data/Fax/Voice/Spkp Modem [2016]" -r01 "GVC Corporation [13e0]" "Unknown device [0219]"
02:02.0 "Multimedia audio controller [0401]" "Creative Labs [1102]" "[SB Live! Value] EMU10k1X [0006]" "Creative Labs [1102]" "Unknown device [1003]"
02:02.1 "Input device controller [0980]" "Creative Labs [1102]" "[SB Live! Value] Input device controller [7004]" "Creative Labs [1102]" "Unknown device [1003]"
02:08.0 "Ethernet controller [0200]" "Intel Corporation [8086]" "82801DB PRO/100 VE (LOM) Ethernet Controller [1039]" -r81 "Dell [1028]" "Unknown device [0142]"
craig@craig-desktop:~$ 


sudo lshw -C network gave me this:> craig@craig-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:b1:10:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.2.7 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:d6:83:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 link=no multicast=yes wireless=IEEE 802.11g
craig@craig-desktop:~$ 


sudo iwlist scan gave me this:

> craig@craig-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:1B:35:13
                    ESSID:"Barb"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:09:5B:AE:55:7A
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

craig@craig-desktop:~$ 


Hopefully you can make something of all that. It's gibberish to me. Thanks for the help!:)

---

### Post by eternal_sage on 2008-10-31
it looks like your device is a 82801DB PRO/100 VE made by Intel, and it seems that the computer is accessing it. hmm. i'm not entirely certain where to go from here (still a bit new myself) but at least anyone with a bit more experience than me will have a bit more information to go on.

is this a 8.10 or 8.04 (or some other version)? 8.10 seems to have alot of issues with wireless.

sorry i can't be of more help, although i'm fairly certain someone will be along soon. this place is abuzz at the moment with very helpful people.

---

### Post by helgman on 2008-11-01
Are you using the network manager or are you using the terminal (or some other tool)?

> *-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:17:3f:d6:83:0c
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.52+Belkin Corporation.,06/01/2 link=no multicast=yes wireless=IEEE 802.11g

That is the wireless card. From the looks of it, the Intel thing is your wired card, correct?

The iwlist command shows that (a) you have a functioning wireless card and (b) what networks are within range (sort of). So now it boils down to "how" you are going to connect.

Once again, the WifiDocs I gave you the links to above should get you on your way. Go through the second "Getting Started with Wireless Networking", although I see now if you use Ubuntu 8.10 there might be some changes to the look-and-feel of stuff.

Post back to as where you get stuck.

Regards,
Helgman

---

### Post by Aiex on 2008-11-02
Well, I gave that a shot. I learned some useful things, but I didn't manage to solve the problem. I know the wirless card is working, it can see other networks and it's associated with the right driver, but I still can't connect to any networks. I tried pinging my router, but that didn't work either. I'm not sure what the problem is now. Any further advice?

---

### Post by eternal_sage on 2008-11-02
does the device have a kill switch of some kind? i know my Inspiron 6000 has the ability to toggle wireless with a [Fn]+[F2] combo. it may sound rather noobish to miss, but i did this exact thing just last week for 4 days (and got quite upset during this time as nothing would fix it). where yours is a usb card, it may not have such a thing (or it may have one, but can only be toggled via software only available for Windows or Mac). its worth checking out at least.

---

