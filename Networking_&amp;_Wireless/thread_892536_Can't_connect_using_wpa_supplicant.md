---
title: "Can't connect using wpa_supplicant"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by fishwebby on 2008-08-17
Hello,

I really hope someone can help me as I've wasted the best part of a day trying to get wireless networking working in Xubuntu. I'm running 8.04, and it was actually working fine (and had been for months) until it suddenly stopped. I assume some automatic update killed it. I was using WEP as I never managed to get WPA working, but I was happy to put up with that. To try and get it working again, I've been through so many forum posts that suggest different things, I'm worried now that my configuration might be in too much of a mess to get it working again (I really don't want to reinstall everything!)

I'll try and explain everything in the hope that someone who knows more about this (I'm still a bit of a Linux noob, especially in command-line land).

Doing this:

```
lspci -v | less
``` (following instructions from [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"))

tells me this:

> 02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys WPC54G-EU version 3 [Wireless-G Notebook Adapter]
        Flags: bus master, fast devsel, latency 64, IRQ 16
        Memory at 28000000 (32-bit, non-prefetchable) [size=8K]

Which apparently is supported in Linux according to [this page]("http://linuxwireless.org/en/users/Drivers/b43").

I was using the Gnome network manager, but managed to find the rather promising Wicd, which I installed. This detects my network ok, but when I click on "connect" it just sits there saying "connecting..." and doesn't connect. I can connect to my network if I remove encryption however, although I don't want to do that. It seems to keep dropping the connection if I do that anyway.

I think it may be a problem with wpa_supplicant - I've followed instructions [here]("http://ubuntuforums.org/showthread.php?t=263136"), [here]("http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/") and lots of others but still no joy. If I type

```
wpa_gui
```

it says "Failed to open control connection to wpa_supplicant.", and if I try and run it manually using

```
sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -ieth1 -Dwext
```

it seems to get stuck in an endless loop of output (and still doesn't work).

In an ideal world I'd like to have WPA2 encryption (all of this works in Windows on the same computer by the way), using Wicd. However, willing to accept WEP if necessary and whatever means to connect to it, as long as it works.

Happy to provide configuration details of anything if requested.

Please help before I start thinking that going back to Windows is an option! :-(

Many thanks in advance, 
Dave

---

### Post by pytheas22 on 2008-08-17
Sorry to hear that you're having trouble.  It's possible that an update gave you a bad version of b43, the driver for your card (at least, the driver that you would be using in Hardy by default; other drivers are available).  Please post the output of these commands so that we can get a better idea of where you are:
```

lshw -C Network
dmesg | grep -e eth -e wlan -e b43 -e ssb -e bcm -e ndis
lspci -nn | grep -i broadcom
iwlist scan
```

Please also tell us the name of the network you're trying to connect to.

wpa_supplicant is only used with WPA connections, not WEP or unencrypted networks, so I don't think it's the problem.  I think there's probably a problem with the wireless driver; if that's the case, it should be easy enough to resolve either by recompiling the b43 driver or switching to a different driver for your card.

---

### Post by fishwebby on 2008-08-17
Hi,

thanks for your reply. Here's the output you requested:

```
> lshw -C Network
description: Wireless interface
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:02:00.0
logical name: eth1
version: 02
serial: 00:18:f8:63:9c:45
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

```
> dmesg | grep -e eth -e wlan -e b43 -e ssb -e bcm -e ndis
[   28.804770] natsemi eth0: NatSemi DP8381[56] at 0xdfdfe000 (0000:01:0c.0), 00:03:0d:04:e8:f4, IRQ 16, port TP.
[   29.552386] Driver 'sd' needs updating - please use bus_type methods
[   29.552631]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   49.535716] eth0: DSPCFG accepted after 0 usec.
[   51.693149] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   51.693162] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   51.693169] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   51.693177] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   51.733189] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   52.078800] b43-phy0: Broadcom 4318 WLAN found
[   52.120781] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   52.120804] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   52.249431] udev: renamed network interface wlan0 to eth1
[   53.042504] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   53.204061] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   53.213514] ndiswrapper: using IRQ 16
[   53.567540] wlan0: ethernet device 00:18:f8:63:9c:45 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   53.567595] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   53.567665] usbcore: registered new interface driver ndiswrapper
[   53.667856] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   53.667952] udev: renamed network interface wlan0 to eth1
[   98.233936] ndiswrapper: device eth1 removed
[   98.234068] usbcore: deregistering interface driver ndiswrapper
[   98.310878] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   98.326807] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   98.336754] ndiswrapper: using IRQ 16
[   98.693758] wlan0: ethernet device 00:18:f8:63:9c:45 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   98.694221] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   98.694530] usbcore: registered new interface driver ndiswrapper
[   98.709763] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   98.709872] udev: renamed network interface wlan0 to eth1
[  113.667328] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  113.667785] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  243.494743] eth0: Autonegotiation advertising 0x5e1  partner 0x41e1.
[  243.494752] eth0: link up.
[  243.494757] eth0: Setting full-duplex based on negotiated link capability.
[  243.495664] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  253.727403] eth0: no IPv6 routers present
[  301.415155] eth0: remaining active for wake-on-lan
[  301.448430] eth0: DSPCFG accepted after 0 usec.
[  301.448448] eth0: link up.
[  301.448458] eth0: Setting full-duplex based on negotiated link capability.
[  312.090981] eth0: no IPv6 routers present
```

```
> lspci -nn | grep -i broadcom
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

```
> iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Scan completed :
          Cell 01 - Address: 00:18:39:A3:BE:5E
                    ESSID:"home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

The network I'm trying to connect to is called "home". If you think it's just a problem with the driver, then I'll try and compile it from source to see if that does anything (to be honest I've tried so many things that I'm not sure how I installed the driver in the first place!).

Cheers
Dave

---

### Post by pytheas22 on 2008-08-17
Thanks for the information.  You have some interesting stuff going on.  First, you're using ndiswrapper.  Is there a reason you're doing that instead of using b43, the native Linux driver, which I think should support your card?

Second, the b43 driver appears to be at least partially loading, which is strange.  If you want to stick with ndiswrapper, try adding these lines to the file /etc/modprobe.d/blacklist and see if it makes a difference:
```

blacklist b43
blacklist ssb
blacklist b43legacy
```

After a reboot, the native driver would be disabled, and a command like "dmesg | grep -e b43 -e ssb" should return nothing.

Also, the system is renaming your wireless interface from wlan0 to eth1.  That's not necessarily a problem, but it's weird, and I think it may have to do with competition for your card between the native Linux driver and ndiswrapper.

So I'd see first if blacklisting the native driver helps.  If not, we can try other things, like either getting rid of ndiswrapper, or trying a different Windows driver inside ndiswrapper.  Your card should definitely be capable of connecting to WPA-secured networks; you should not be having to sacrifice that in order to use wireless.

---

### Post by fishwebby on 2008-08-18
Hi,

I tried what you suggested, adding those lines to /etc/modprobe.d/blacklist and rebooting, but that didn't work. There was already a line at the end of that file that was ```
blacklist bcm43xx
``` which might have had something to do with the problem perhaps?

However, as you mentioned that there is a native driver (no, there's no reason that I was using ndiswrapper - although I seem to remember reading somewhere that the native driver is fairly recent, so maybe that's how I had it configured before), I tried uninstalling ndiswrapper (following the instr instructions [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/")) and now it works! :-D

Well, I've rebooted and it seems to connect automatically and no problems yet. The only thing is I don't seem to have completely removed ndiswrapper, as one of the messages on bootup is something like "FATAL ERROR... can't load ndiswrapper" (it flashes past too quick for me to see) - although this isn't causing a problem, is there a logfile I can look at to see exactly what the message is? I suspect it's whatever loads ndiswrapper complaining as it can't find the files.

So it looks like I'm up and running - thank you very much for your help, very much appreciated! :-)

---

### Post by pytheas22 on 2008-08-18
I'm glad it's working.  I'm not sure which driver you're using, since you say that b43 and bcm43xx are both on the blacklist, but at least it's fixed.

> Well, I've rebooted and it seems to connect automatically and no problems yet. The only thing is I don't seem to have completely removed ndiswrapper, as one of the messages on bootup is something like "FATAL ERROR... can't load ndiswrapper" (it flashes past too quick for me to see) - although this isn't causing a problem, is there a logfile I can look at to see exactly what the message is? I suspect it's whatever loads ndiswrapper complaining as it can't find the files.

I suspect that it's trying to load ndiswrapper because your /etc/modules file says to.  You can check the full error message by looking at your system log; go to System>Preferences>System Log, or just open the file /var/log/syslog in a text editor.

If you run into any more trouble, let us know.

---

### Post by fishwebby on 2008-08-19
Hi,

I forgot to mention I removed all the b43* lines from the blacklist, so I suppose it's using the native driver now. Can't find any reference to ndiswrapper in the log you mention, and I've commented out the ndiswrapper lines in /etc/modules, but to be honest I'm happy to not worry about it too much as it's working now (if it ain't broke...).

Thanks again! :-)

Cheers
Dave

---

