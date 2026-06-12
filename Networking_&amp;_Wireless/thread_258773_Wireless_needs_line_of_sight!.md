---
title: "Wireless needs line of sight!"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Poirot on 2006-09-16
Hello,

I am online using wireless now but when I move my desktop away from the router it cannot connect. I have a laptop running XP and it doesn't have any problems, so I presume it's not a problem with the router, it even works upstairs where my dektop belongs.

here are some details:
```
poirot@poirot-desktop:~$ lspci | grep Broadcom\ Corporation 
0000:02:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
```
poirot@poirot-desktop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth1
       version: 02
       serial: 00:11:50:ec:eb:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-amd64-generic ip=192.168.2.4 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e2000000-e2001fff irq:11

```
```
poirot@poirot-desktop:~$ lsmod | grep bcm
bcm43xx               127244  0
ieee80211softmac       32640  1 bcm43xx
ieee80211              39240  2 bcm43xx,ieee80211softmac

```
```
poirot@poirot-desktop:~$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"my network"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:17:3F:0D:2B:A8
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=183/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
poirot@poirot-desktop:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:0D:2B:A8
                    ESSID:"my network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-157 dBm
                    Extra: Last beacon: 396ms ago


```
```
poirot@poirot-desktop:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:11:50:EC:EB:ED
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feec:ebed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1378 errors:0 dropped:13 overruns:0 frame:0
          TX packets:1687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1269339 (1.2 MiB)  TX bytes:185869 (181.5 KiB)
          Interrupt:11 Base address:0x8000

```

Is there anything obviously wrong here? I use the bcm43xx driver and got the firmware through cm43xx-fwcutter. This has been very frustrating.

Thanks

---

### Post by 51m0n on 2006-11-29
I get exactly the same behaviour. 

ndiswrapper had same range as Xp, BCM43xx driver has an issue whereby anything less than perfect connection is deemed pants. 

I found this;-
[http://dev.gentoo.org/~dsd/genpatches/trunk/2.6.18/2400_bcm43xx-signal-quality.patch](http://dev.gentoo.org/~dsd/genpatches/trunk/2.6.18/2400_bcm43xx-signal-quality.patch)

but wouldn't know how to port it into (k)ubuntu :(

---

