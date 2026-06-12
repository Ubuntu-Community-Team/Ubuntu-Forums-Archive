---
title: "Wireless Troubles with D-Link WNA-2330"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Sunflower1970 on 2007-02-24
I've been reading and reading for the past week on how to get my wireless working in my laptop with Edgy (and/or Feisty. Tried both of them). A Thinkpad R40. The card I have for it is the D-Link WNA-2330 with the Atheros AR5212 chipset. Oddly enough, the wired ethernet won't work either, so the computer has no internet connection whatsoever.

Whatever I have to do it will have to be downloaded from my desktop with the working connection, then transferred over using my USB flash drive. 

Right now it has a fresh install if Edgy on it, no updates whatsoever, so I'm using kernel 2.6.17-10-generic. 

I feel I'm close to the answer...but just not there yet. 

here's the output of iwconfig:
```
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"removed my network name"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Here's my dhclient:
```
carrie@carrie-laptop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:74:33:f1
Sending on   LPF/ath0/00:15:e9:74:33:f1
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database – sleeping.
```

my lspci:
```
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

my lsusb:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

and lspci -v:
```
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
        Subsystem: IBM Unknown device 0522
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8000 [size=64]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1a
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at d2000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```

Would my not being able to connect have anything to do with this madwifi 'bug' that I had been reading on? I do have WEP enabled. Haven't tried without WEP yet...since the other computer I have hooked up wirelessly is in use at the moment. 

I read this page: [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016) but I'm not too sure I understand what the answer is. I did download the newest madwifi madwifi-0.9.2.1.tar.gz (if that is the answer...and I don't even know if it is)...but compiling it seems to be beyond me...I'm not too sure where I can download any of the tools for compiling which would be in a .deb package that I could transfer over. 

In the network settings in Edgy, I entered all the settings I needed for ath0, but still cannot connect.

When I tried Feisty, I could see the networks (I could see my own, and my neighbor's wireless), but it wouldn't let me connect to mine.

It's so frustrating. Up until trying to get this laptop to work, I've had no troubles at all with my two desktops. Everything worked flawlessly (well a few bumps here and there, but all were easily fixable). This is the first time I've really run up against a brick wall...

---

### Post by Floppyjoe on 2007-02-24
Have you installed linux-restricted-modules for your kernel? If you click on System/Administration/Synaptic Package Manager. Then Click on Edit/ADD CDROM. Then use your Ubuntu install cd here.Then click reload. Then search for linux-restricted-modules.

---

### Post by Sunflower1970 on 2007-02-24
Tried it, and it's showing the restricted modules are already in my system. 

When I tried a search for madwifi, I show something's already installed under /lib/modules/2.6.17-10-generic/madwifi

---

### Post by Thanol on 2007-02-24
If all else fails, try Dapper.  It comes with madwifi preinstalled

---

### Post by Floppyjoe on 2007-02-24
What does your /etc/network/interfaces file look like?

---

### Post by Sunflower1970 on 2007-02-25
> **Floppyjoe said:**
> What does your /etc/network/interfaces file look like?

I ended up screwing something up so I decided just to do a fresh install (again) Anyway, the file looks like this:

```
carrie@carrie-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp


auto eth0

iface ath0 inet dhcp
wireless-essid xxxxxxxxxxx Network
wireless-key xxxxxxxxxx

auto ath0
```

---

