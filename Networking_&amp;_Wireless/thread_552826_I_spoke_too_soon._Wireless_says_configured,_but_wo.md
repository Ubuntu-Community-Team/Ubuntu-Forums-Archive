---
title: "I spoke too soon. Wireless says configured, but won't work."
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by rast4man on 2007-09-17
So I did a fresh install (again) of Kubuntu 7.04. I did a removal/install of Ndiswrapper 1.38 and installed 1.47 from scratch while loading the XP NETw4x32.INF file with NDIS. The networks don't show up in Knetworkmanager but I can do a 'iwlist scan' and all of my networks show up. (I have multiple wireless setup in my house) I have the hardware switch on and the wireless enabled, but I can only connect to the net when I'm hard wired in. Here is some info and any help is certainly appreciated.

> rast4@NiXiN:~$ ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present


> rast4@NiXiN:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:4353] (rev 14)
03:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4229] (rev 61)
07:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
07:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
07:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

> rast4@NiXiN:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:73:6c:9e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:f0600000-f0603fff ioport:2000-20ff irq:17
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:10:c4:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.47+Intel,04/30/2007,11.1.1.11 ip=192.168.1.112 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f0700000-f0701fff irq:16


> rast4@NiXiN:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=150 Mb/s
          Fragment thr=1500000 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> rast4@NiXiN:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:84:80:96
                    ESSID:"EDITED"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:66:0C:40:82
                    ESSID:"EDITED"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1C:10:32:B6:A2
                    ESSID:"EDITED"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:100/100  Signal level:-27 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Any help would again be appreciated. I'm stuck and frustrated.

The computer is a Toshiba A205-S4607 with the Intel Wireless 4965 A/G/N chip.

Any other info needed, please ask.

---

### Post by spd106 on 2007-09-18
I think the most likely way you will get it working is to upgrade to Gutsy, it's not really ready for prime time use yet, but I've read that it has support for the 4965agn card. If you can manage to wait another month or at least until the beta is released on 24th, that would be better.

Otherwise you'll have to either compile your own kernel with iwlwifi [http://intellinuxwireless.org/](http://intellinuxwireless.org/) or struggle on with ndiswrapper. It is reported to work, but as you have seen it's not easy.

I don't have one of these cards so I can't really speak with any authority. But I am interested to hear of any progress you make.

---

### Post by rast4man on 2007-09-18
Thanks for the reply. Oddly, I started off with the Gutsy Beta. I didn't find the support for the card to be satisfiable. I'm tired of limping along with NDIS though. *sigh* I've read too many posts reporting the same problems and the truly sad thing is that I had it working flawless at one point. :(

---

