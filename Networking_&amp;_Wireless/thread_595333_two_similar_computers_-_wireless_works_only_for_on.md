---
title: "two similar computers - wireless works only for one"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by MichaëlVD on 2007-10-28
I have an iMac and a Dell Inspiron 5100. I can get online wirelessly with the iMac, but not with the Inspiron. And yet, I don't see any important differences in their setup.

Both run gutsy.

First, some config files for the iMac (which work)

ifconfig > ifconfig.txt:

```
eth0      Link encap:Ethernet  HWaddr 00:17:F2:C3:87:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:17:F2:C3:87:50  
          inet addr:169.254.7.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61748 (60.3 KB)  TX bytes:61748 (60.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:E3:09:AF:B1  
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe09:afb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33609054 (32.0 MB)  TX bytes:2597893 (2.4 MB)
          Interrupt:17 Memory:88200000-88204000 

```

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp
```

iwconfig > iwconfig.txt
```
wlan0     IEEE 802.11g  ESSID:"Apple Network 20b853"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:63:20:B8:53   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The the Inspiron, for which wireless does not seem to work:

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:E7:34:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:DB:E7:34:D1  
          inet addr:169.254.9.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14672 (14.3 KB)  TX bytes:14672 (14.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:2C:8C:A2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4914 (4.7 KB)
          Interrupt:11 Base address:0xc000 
```

/etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0

auto eth1

auto eth2

auto ath0

auto wlan0

iface eth0 inet dhcp
```

iwconfig > iwconfig.txt

```
wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any advice is very much appreciated!

---

### Post by MichaëlVD on 2007-11-01
My laptop is still sitting there as a wireless-less brick, so if anyone could help me out, that would be very much appreciated. Luckily, my other computer works just fine, so it's not that I'm completely disconnected from the virtual worlds around me!

Thanks

---

