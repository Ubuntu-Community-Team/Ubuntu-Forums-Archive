---
title: "wifi issues... lots of them"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by Amt0571 on 2007-01-26
Hello,

I have a system running Edgy which has an rt61 wifi from conceptronic and an ethernet card from realtek.

Following the tutorial on this forums I've installed the rt61 card and it detects the access point correctly.

First, I tried with WPA, that is what I'm running in my router (a 3Com 11g), but I had no luck altough I followed this tutorial [http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=rt61) instructions step by step. When I did a scan it detected the access point, but refused to connect to it.

Then, I decided to switch to WEP... and changed the configuration accordingly, but it still refused to connect to the access point.

Finally, I tried to connect using GTKWifi, and it connected ok (I also checked this in the router admin page), but the internet connection was not working (even with the RJ45 cable connected!).

So I ended up with a broken network... I managed to repair the wired connection by disabling the wireless one... but when I activate wireless, the network stops working altough I have the wired connection plugged in (I have assigned different IPs to the wireless and wired, of course).

Also, when I start the system with no network connections, gnome loads very very very very very sloooooooooooooooow... 

This slow issue happened to me at first and I solved it by editing some lines on /etc/hosts but now it's slow even with the edited file.

Is the any solution apart from apt-get install fedora (which I'm about to do since Edgy has only given me headaches)?

Well, just in case I post my configuration files:

/etc/network:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth0 inet dhcp
auto eth0

iface ra0 inet static
address 192.168.1.8
netmask 255.255.255.0
gateway 192.168.1.1
auto ra0
```

rt61sta.dat (configured for WPA):

```
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=bnn
NetworkType=Infra
Channel=6
AuthMode=WPAPSK
EncrypType=WPA
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=475bgg578
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0
```

/etc/hosts:

```
127.0.0.1 localhost mediacenter.bnn

```

Thanks in advance

---

### Post by Amt0571 on 2007-01-27
Ok... I've solved it by disabling eth0 from BIOS... it's a solution for now since I don't need wired access on that system. However, if someone has a solution which lets me have both adapters working, I would highly appreciate it.

---

