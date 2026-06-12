---
title: "Pro/Wireless 3945 ABG (Centrino) weak signal with 8.04"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Mickser_52 on 2008-11-20
I am having a problem with wireless networking. The wireless network is only detected if I am beside the router. I can then connect to internet and move to another room and stay connected e.g. at the moment in another room the connection is saying 68%. When I booted in this this room it could not detect the network at all.

I have a windows xp partition which picks up the signal in any room in the house. I would be grateful for any help.

---

### Post by darco on 2008-11-20
Well if XP connects w/o a prob then we can rule out ethernet card. When you are connected in Ubuntu, is the signal ever stronger than 68%? What encryption are you running? When you are in another room, does network manager see your ssid?. Run this command and post results:

```
iwconfig
```

good luck

darco

---

### Post by Mickser_52 on 2008-11-20
Thanks for reply, if encryption means for wireless it is bin hex. Connection varies in room with rooter it is 92%, at present, where I am working (20 feet away)  it is 74%.but I still had to move in order to pick up signal? 

here is result of iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"xxxxxxxxxxxxx"  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: zzzzzzzzzzzzzzz  
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=75/100  Signal level=-60 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Have just installed ubuntu and have a lot to learn

---

### Post by darco on 2008-11-20
lets run this command to see your hardware:

```
lspci
```

darco

---

### Post by Mickser_52 on 2008-11-21
I have been having fun? Thought I'd try wicd this didn't work at all. Didn't know how to get nm applet back, tried transferring from my wubi install with LVPM and messed up entire startup so had to do a clean install from cd. But back to where I was again. Here is list

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


```

Learning by my mistakes I hope

---

### Post by darco on 2008-11-22
Why not install 8.10? It has better wl support. Another alternative is Linux Mint...You could download the Live CD and see if your wl works out of the box (this is for both Mint and Intrepid)

darco

*edit*
did you do a search on your wl card? Seems to be alot of issues with and hopefully resolutions.

---

### Post by Mickser_52 on 2008-11-22
Thanks for your help. I will try 8.10 in the near future. I have been getting more consistent results by moving to a particular area. The difference when compared to XP is that with XP I can connect when the signal strength is low.  

Long term I would like to continue with Ubuntu and so far this is the only problem I have encountered. Future releases will hopefully bring improvements.

---

