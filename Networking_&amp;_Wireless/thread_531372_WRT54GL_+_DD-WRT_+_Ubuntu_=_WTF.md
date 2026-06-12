---
title: "WRT54GL + DD-WRT + Ubuntu = WTF?"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by Apocrathia on 2007-08-21
okay so im using a wrt54gl v1.1 loaded with dd-wrt v23 sp2.
i have 4 other computers in my house (xp systems) and they all connect to this router perfectly. (2 wired 3 wireless)
i setup a dual boot on my laptop because im really thinking of making a gradual migration over to ubuntu. however, it doesnt help much when my laptop doesnt connect to my router (although ubuntu did recognize my wireless card this time, big plus not to have to deal with ndiswrapper)
anyone have any clue wtf is going on with this and why its not working? i have an ssid broadcasted, wpa protected network. and the network wont even show up. i manually input the info and it wont connect.
im guessing theres some sort of handshake issue. but does anyone know how to solve this, other than going back to the linksys firmware? possibly openwrt or hyperwrt?

---

### Post by nosrednaekim on 2007-08-21
I doubt the problem is with your router... but rather your card.

try temporarily taking the encryption off and attempt connecting and report what happens.

also provide the outputs of "lspci" and "iwconfig"

---

### Post by Apocrathia on 2007-08-21
heres the readout
```
apocrathia@Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

```

```
apocrathia@Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

tried disabling all of the encryption, still nothing. the AP doesnt even show up :(

---

### Post by Apocrathia on 2007-08-22
nvm found my problem. i installed the bcm43xx driver [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133]("http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133")
and everything works perfectly. thanks for showing me the lspci command nosrednaekim.

---

### Post by nosrednaekim on 2007-08-22
yup, No problem. Glad you got it working.

---

