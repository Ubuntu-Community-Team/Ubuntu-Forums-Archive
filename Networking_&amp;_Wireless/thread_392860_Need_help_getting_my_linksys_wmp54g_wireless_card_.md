---
title: "Need help getting my linksys wmp54g wireless card to work"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by redtrak on 2007-03-25
I'm a linux noob trying to get a wireless card (linksys wmp54g) to work.  I tried to use ndiswrapper, that didn't fix the problem, but I'm not positive I used it right.  Not sure what info you guys need; I am trying to connect to a linksys wrt54g with WEP security enabled as well as a mac filter.  When I boot Vista it works great so I know the router and card are working.

lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)
0000:00:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"dd-wrt2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:7D:9E:B5
          Bit Rate:54 Mb/s   Tx-Power:-3 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=66/100  Signal level=-53 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2560298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2560298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:208486821 (198.8 MiB)  TX bytes:208486821 (198.8 MiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:64:91:FA
          inet6 addr: fe80::212:17ff:fe64:91fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49326 errors:696 dropped:696 overruns:0 carrier:0
          collisions:2276 txqueuelen:1000
          RX bytes:13242641 (12.6 MiB)  TX bytes:3349372 (3.1 MiB)
          Interrupt:193 Base address:0xc000

---

### Post by handaxe on 2007-03-25
Outputs look normal at first glance - card is seeing the AP and is transmitting and receiving.

The following tutorial has been recommended for wep (tnx chili555 for the recommendation)

[http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

Best advice if you have control over the router is to disable all encryption, prove the connection, then enable wep, prove the connection, enable mac filter etc. Also, do not have a wired connection running.

HA

btw, preceding iwconfig with sudo produces more info.

equally, ```
sudo iwlist  ra0 scan
``` provides info on APs etc

---

### Post by redtrak on 2007-03-25
Thanks!!! problem solved.
For some reason my key was set up like this;
wireless-key s:************
changed it to wireless-key ************ and now it works great.

---

### Post by handaxe on 2007-03-25
Hi,

the s: format is used to send an ascii passkey to the router.  Without it it is sent as hex.

HA

---

