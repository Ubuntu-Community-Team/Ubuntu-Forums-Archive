---
title: "Asus 1215B, Atheros AR9285"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by sangief on 2014-04-20
Hi!

I'm having some issues with my wireless interface. A couple of days ago, I was using my notebook in a standard way (web browsing, programming, etc) and suddenly everything froze (back then I had Ubuntu 13.10, but I upgraded recently). I had to manually turn off the notebook by pressing the power button for a short time. When I rebooted, my wireless interface was gone (that is, wlan0 completely missing). After rebooting again, everything was looking good as usual, but unfortunately the system froze again after 10 minutes or so. This pattern continued for ever. I tried uprgrading Ubuntu, and now I have Ubuntu 14.04 LTS. The system does not seem to freeze now, but nevertheless the wireless issues are still there. After a bunch of minutes being successfully connected to my wireless network, Ubuntu disconnects from it and wireless is lost for ever (I can't even do a scan with iwlist). 

Anyone can help, please? I tried compiling and reinstalling the ath9k driver, but I had no luck, and I really don't know what else I can do. Here I post some data that may help:

lspci -nn output:
```

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] [1002:9806]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1512]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1513]
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]

```

sudo lshw -C network output:
```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:4d:b3:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fea00000-fea0ffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: 54:04:a6:18:ba:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fe900000-fe93ffff ioport:e000(size=128)

```

dmesg | grep ath output:
```

[    2.173154] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[   19.240758] ath: phy0: ASPM enabled: 0x42
[   19.240769] ath: EEPROM regdomain: 0x60
[   19.240772] ath: EEPROM indicates we should expect a direct regpair map
[   19.240778] ath: Country alpha2 being used: 00
[   19.240781] ath: Regpair used: 0x60

```

dmesg | grep wl output:
```

[   21.488605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.493500] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.692956] wlan0: authenticate with c0:c1:c0:0b:8f:2c
[   22.709658] wlan0: send auth to c0:c1:c0:0b:8f:2c (try 1/3)
[   22.712659] wlan0: authenticated
[   22.715953] wlan0: associate with c0:c1:c0:0b:8f:2c (try 1/3)
[   22.720264] wlan0: RX AssocResp from c0:c1:c0:0b:8f:2c (capab=0x411 status=0 aid=4)
[   22.720366] wlan0: associated
[   22.720425] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  159.108508] wlan0: deauthenticating from c0:c1:c0:0b:8f:2c by local choice (reason=3)
[  163.188295] wlan0: authenticate with c0:c1:c0:0b:8f:2c
[  163.210471] wlan0: send auth to c0:c1:c0:0b:8f:2c (try 1/3)
[  163.213361] wlan0: authenticated
[  163.216088] wlan0: associate with c0:c1:c0:0b:8f:2c (try 1/3)
[  163.220210] wlan0: RX AssocResp from c0:c1:c0:0b:8f:2c (capab=0x411 status=0 aid=4)
[  163.220310] wlan0: associated
[  163.272165] wlan0: deauthenticating from c0:c1:c0:0b:8f:2c by local choice (reason=2)
[  163.281461] wlan0: authenticate with c0:c1:c0:0b:8f:2c
[  163.298332] wlan0: send auth to c0:c1:c0:0b:8f:2c (try 1/3)
[  163.303298] wlan0: authenticated
[  163.308110] wlan0: associate with c0:c1:c0:0b:8f:2c (try 1/3)
[  163.314663] wlan0: RX AssocResp from c0:c1:c0:0b:8f:2c (capab=0x411 status=0 aid=4)
[  163.314750] wlan0: associated
[  321.887625] wlan0: deauthenticating from c0:c1:c0:0b:8f:2c by local choice (reason=3)

```

uname -a output:
```

Linux knuth 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

By the way, the wired Ethernet connection works as expected (I'm posting this using it).


Thanks in advance for your time!!!

---

### Post by varunendra on 2014-04-22
If you haven't already, please try -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
..followed by a reboot, or -
```
suod modprobe -rv ath9k
sudo modprobe -v ath9k
```
If it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by sangief on 2014-04-22
Thanks!! Unfortunately, though, your suggestion didn't work. My connection dropped after about 15 minutes...
I ran the script provided, and I attach the results here. I really hope you could help me. Thanks again!!

---

### Post by varunendra on 2014-04-23
A few more suggestions -

1) Channel 11 seems too crowded, try changing to channel 1 or 6 in the router/access-point.

2) Try changing the Access-Point's SSID to something that does not contain blank spaces or special characters. Underscores are okay.

3) Try explicitly declaring your country code for Regulatory Domain (regdomain) settings. For example, if you are located in US, try -
```
sudo iw reg set US
```
To find your country code for wifi regdomain settings, please refer to this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

4) Since you are already using kernel 3.13, I don't see a point in using compat drivers of the same series. I suggest you uninstall the compat drivers, and report back with the default driver + the above suggestions applied. I haven't tried this myself, but I think the following command should uninstall the compat drivers (run from the same directory where you ran "make" and "make install" commands) -
```
sudo make uninstall
```

If these don't help, we may try a newer version of compat drivers. Although I can confirm that I have exactly the same card, and it is working very nicely with the default driver in kernel 3.2.0-36-generic (yeah, I'm still on that older kernel). Don't mean to say you need to downgrade, but maybe we could try the older driver if that is possible at all!

---

### Post by sangief on 2014-04-24
Well, here we go again. I tried to do everything you suggested but the problem is still there. Looks like the system freezes when I'm quite close to the access point...
I'm attaching here two different outputs of the script: one obtained just after rebooting when Ubuntu froze (you will see that the wireless interface is completely gone there), and the other one obtained after rebooting again, with everything looking normal.

Any other idea...?

---

### Post by sangief on 2014-04-24
One more thing. A couple of days ago I tried to compile an older ath9k driver, but I couldn't do it (several errors that, I guess, are due to a different kernel version). Since I really don't have experience doing this, maybe I'm missing something. I'd like to try an older driver; I think that maybe that could solve the problem. How can I do it??

Last note: 2 minutes ago I moved to the other room, where the access point is. Ubuntu froze almost immediately. Moreover, every time it froze I think it was there. Thus, maybe it is reasonable to assume that being close to the access point messes things up. However, I don't have a clue about why... could it be broken and thus sending junk packets that make the driver crash? It is about 2 and a half years old. Just in case, it is a Linksys WRT310N router.

---

### Post by varunendra on 2014-04-24
A PCI card completely missing even in "lspci" looks like a hardware issue to me, although the chances of it being a software bug can't be denied.

Assuming the card is located in a User-Accessible area (usually beneath a removable panel at the bottom of laptops), can you check if it is over heating or if it seems loose? If you can, just unscrew it > pull it out > clean its contacts with a clean cloth > re-seat and fix with the screws. Make sure the antenna contacts are firm.

Or, before going hardware mode, can you download an older ISO ant test it in Live mode? If it is a software issue, it should work nicely with the older kernel as it does here for me.

Links for older ISOs : [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

I recommend original 12.04, or 12.04.1, whichever has kernel 3.2. I also recommend to download via torrent to ensure the integrity of the ISO *(but sometimes a direct download is more reasonable if a torrent is nearly dead due to few or no seeders).*

---

