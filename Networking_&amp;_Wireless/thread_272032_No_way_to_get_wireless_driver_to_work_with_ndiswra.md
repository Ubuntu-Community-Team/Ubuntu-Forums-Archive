---
title: "No way to get wireless driver to work with ndiswrapper"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by darkrad on 2006-10-05
Hello, i just installed dapper 6.06 and wanted to setup wireless on my acer aspire 1610.
I followed the tutorial to do that and i was able to setup it when i did in the past on ubuntu. not this time. i downloaded ndiswrapper version 1.25 but when i launch the install command i got a perl debug console.. so i installed ndiswarapper 1.23 but all the drivers i tried i get:
```
Installed drivers:
bcmwl5a invalid driver!
```
I give you some more info on my system, so you can try to tell me what i'm doing wrong ](*,) 
```
paolo@paolo:~$ uname -r
2.6.15-27-386
```
```
paolo@paolo:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:EF69-E197-3D49-D76A-4892-D747-9B   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
```
paolo@paolo:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:03:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:03:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:03:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:03:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:03:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```
```
0000:00:00.0 0600: 8086:2570 (rev 02)
0000:00:01.0 0604: 8086:2571 (rev 02)
0000:00:1d.0 0c03: 8086:24d2 (rev 02)
0000:00:1d.1 0c03: 8086:24d4 (rev 02)
0000:00:1d.2 0c03: 8086:24d7 (rev 02)
0000:00:1d.3 0c03: 8086:24de (rev 02)
0000:00:1d.7 0c03: 8086:24dd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev c2)
0000:00:1f.0 0601: 8086:24d0 (rev 02)
0000:00:1f.1 0101: 8086:24db (rev 02)
0000:00:1f.3 0c05: 8086:24d3 (rev 02)
0000:00:1f.5 0401: 8086:24d5 (rev 02)
0000:00:1f.6 0703: 8086:24d6 (rev 02)
0000:01:00.0 0300: 1002:4e50
0000:03:04.0 0607: 104c:ac8e
0000:03:04.1 0607: 104c:ac8e
0000:03:04.2 0c00: 104c:802e
0000:03:05.0 0200: 10ec:8139 (rev 10)
0000:03:06.0 0280: 14e4:4320 (rev 03)
```

obviously i downloaded from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) the drivers with BCM4306 14e4:4320 as details.

when i try to install a driver this happen:
```
paolo@paolo:~$ sudo ndiswrapper -e bcmwl5a
paolo@paolo:~$ ndiswrapper -l
No drivers installed
paolo@paolo:~$ cd Desktop/
paolo@paolo:~/Desktop$ sudo ndiswrapper -i bcmwl5a.inf 
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
paolo@paolo:~/Desktop$ ndiswrapper -l
Installed drivers:
bcmwl5a invalid driver!
paolo@paolo:~/Desktop$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
paolo@paolo:~/Desktop$ sudo ifup eth1
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth1.
```

Really haven't a clue of what to do ](*,) ](*,) ](*,) 
Any ideas? :confused:

---

### Post by darkrad on 2006-10-05
ok, this thread answer my questions: [http://ubuntuforums.org/showthread.php?t=157157&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=157157&highlight=broadcom)
thanks anyway

---

