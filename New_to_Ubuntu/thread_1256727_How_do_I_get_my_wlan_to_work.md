---
title: "How do I get my wlan to work?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by burtzacarach on 2009-09-03
Hi, I'm trying to get my wireless ad-hoc network set up so I can use my iPhone as a VLC media player remote, but I seem to be having a problem getting any wireless connection to appear in my Network Manager.

```
zac@alpine-mobile:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
zac@alpine-mobile:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8185 : driver installed
	device (10EC:8185) present (alternate driver: rtl8180)
zac@alpine-mobile:~$ 
```

```
zac@alpine-mobile:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:0314]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:1314]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:2314]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:4314]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:7314]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:0c.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
00:0c.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
00:0c.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
00:0e.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] [1106:3344] (rev 01)
zac@alpine-mobile:~$ 
```

```
zac@alpine-mobile:~$ sudo lshw -C Network
[sudo] password for zac: 
  *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wlan0
       version: 20
       serial: 00:c0:a8:bf:68:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.53+Realtek,11/30/2005,5.104.11 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:03:25:3a:72:41
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=16 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ee:26:f1:de:c0:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
zac@alpine-mobile:~$ 
```

```
zac@alpine-mobile:~$ uname -m
i686
zac@alpine-mobile:~$
```

From all of this, it seems to me like everything is in order, granted I am no programmer, and also I can set up wireless networks but they do not appear in the Network Manager:
[IMG]http://farm3.static.flickr.com/2674/3883535864_451a914f3b.jpg[/IMG]

I really enjoy being able to control my music, volume and playlists from anywhere in the house, but what am I doing wrong?

Thanks for any help, I tried to give as much information to being with as possible for you all:o

---

### Post by Shig on 2009-09-03
Hi There,

You can try the steps [here]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") to hopefully get this working in AdHoc mode.
There is also good documentation on the Ubuntu Community Documentation site for AdHoc networks [here.]("https://help.ubuntu.com/community/WifiDocs/Adhoc")

---

