---
title: "broadcom card problems"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by bmbeeman on 2007-01-14
I'm trying to get wireless working on my Acer Aspire laptop and I ran across a tutorial at [DebianAdmin.com]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") and followed the instruction. and it had no effect, I'm still back where I started.  Anybody got any other ideas?

---

### Post by Floppyjoe on 2007-01-14
What is your wireless cards chipset?

```
lspci
```

What is the output of:
```
iwconfig
```

What is in your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```

There are some good howto's in the tricks,tips and howto's section

---

### Post by thoman on 2007-01-19
Iam having the same problem too..

mine was
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Ho

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"pcsbwbd"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


auto lo
iface lo inet loopback


address 170.38.43.88
netmask 255.255.255.192
gateway xx.xx.xx.xx


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ppp0 inet ppp
provider ppp0








iface eth1 inet dhcp
address 170.38.43.88
netmask 255.255.255.255
gateway xx.xx.xx.xx
wireless-essid pcsbwbd

iface eth0 inet static
	address 170.38.43.88
	netmask 255.255.255.192
	gateway xx.xx.xx.xx




auto eth0

auto eth1


help me too.......:-?

---

### Post by Floppyjoe on 2007-01-19
> **thoman said:**
> Iam having the same problem too..

mine was
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Ho

help me too.......:-?

Thoman, your wireless card is:
> 00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Here is a Howto i followed to get mine to work:

[http://www.ubuntuforums.org/showthread.php?t=197102]("http://www.ubuntuforums.org/showthread.php?t=197102")
Hope this helps.

---

### Post by thoman on 2007-01-19
Thanks a lot
can wait to boot to my ubuntu.......

but i hav to wait till i get to my office to get my live cd.....

---

### Post by teaker1s on 2007-01-19
or there is a good howto in my signature

---

