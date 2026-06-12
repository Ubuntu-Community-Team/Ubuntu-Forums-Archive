---
title: "Wireless adapter US Robotics 5423 Problem"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Neopard on 2006-12-26
Hi Everybody
I have a HUGE problem with usb wireless adapter ](*,)
Mi dongle is model 5423 from US Robotics. **It works correctly on WinXP**
I'll report every step i did to have connection working on my PC

In installed last ndiswrapper version (1.32, building source from [ndiswrapper page](http://ndiswrapper.sourceforge.net)), since my usb dongle isn't natively supported by my Ubuntu Installation (I have Edgy 6.10).
Actually my model (5423) is not in the supported models [list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List), but model 5421 and 5422 are, so I tried.

I installed usb drivers (**ndiswrapper -i usrwgu.inf**) and moprobed **ndiswrapper**
Checked everything's ok
```
neopard@enterprise:~$ ndiswrapper -l
usrwgu : driver installed
        device (0BAF:0121) present

```

Checked my USB dongle sees my access point correctly (**iwlist wlan0 scan**):
```
neopard@enterprise:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:9A:7C:DC:22
                    ESSID:"xxxxxxx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

Finally i tried to connect to my AP (Which has a 64bit hex WEP encryption). Here's the output of **sudo ifup wlan0**:
```
neopard@enterprise:~$ sudo ifup wlan0 
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:c1:32:ba:9f
Sending on   LPF/wlan0/00:14:c1:32:ba:9f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I'll write here all ouput code which can contain useful informations far anyone to help me. Most of all, the first one has a very strange value for Tx-Power (it's the output for **iwconfig**):

```
neopard@enterprise:~$ iwconfig

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:**-2147483648 dBm**   Sensitivity=0/3  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Obviously that value for Tx-power has something really strange.. I don't know very well how wireless networking works, it looks like my dongle has no transmit power, but I was wondering if it makes any sense since it sees correctly my ap, as shown in **iwlist wlan0 scan** output code (but this might be related jut with data receiving..)

More output code:

**/etc/network/interfaces**:

```
auto lo
iface lo inet loopback

iface rausb0 inet dhcp
wireless-essid xxxxxxx
wireless-key xxxxxxxxxx

auto rausb0

iface wlan0 inet dhcp
wireless-essid xxxxxxx
wireless-key xxxxxxxxxx

auto wlan0

```

(rausb0 is another usb dongle which a friend of mine lent to me to test if I have any problem with wireless support in general.. but it worked fine, it's a SPARKLAN dongle natively supported by my installation)

**dmesg** output:

```
[17179812.824000] ndiswrapper version 1.32 loaded (preempt=no,smp=no)
[17179812.976000] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[17179813.160000] ndiswrapper: driver usrwgu (USR,02/15/2006,6.3.4.16) loaded
[17179814.452000] wlan0: ethernet device 00:14:c1:32:ba:9f using NDIS driver: usrwgu, version: 0x6030410, NDIS version: 0x501, vendor: 'USRobotics Wireless USB Adapter', 0BAF:0121.F.conf
[17179814.508000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179814.508000] usbcore: registered new driver ndiswrapper
[17179814.512000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17180379.692000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17180482.788000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

**ifconfig** output:
```

neopard@enterprise:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:AD:0C:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:C1:32:BA:9F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Anyone can help? I did lots of searches on google and forums but it looks like I'm the only one in the world with this problem (or at least the only one who bought this cursed dongle and tried to make it work on Linux :D)
Thanks in advance for any suggestion

---

### Post by BenXX on 2007-01-03
Hello,

The 5423 wireless adapter from USRobotics is a Zydas 1211B chipset (0baf:0121).
It works with drivers from [http://zd1211.ath.cx/]("http://zd1211.ath.cx/") with Wep enabled.

I've tested it with Wpa but it does not work correctly.

---

