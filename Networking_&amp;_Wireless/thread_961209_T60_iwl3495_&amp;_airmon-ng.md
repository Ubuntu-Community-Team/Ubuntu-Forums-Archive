---
title: "T60 iwl3495 &amp; airmon-ng"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-10-28
I'm having problems getting my wireless card to follow the tutorial on [Aircrack-ng.org](http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients).  Each time I try the first part of the tutorial I get this (I included a copy of my ifconfig):
```

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:68:21:a7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:6bff:fe68:21a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:135785 (132.6 KB)  TX bytes:57983 (56.6 KB)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88900 (86.8 KB)  TX bytes:88900 (86.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:4a:1c:03  
          inet6 addr: fe80::213:2ff:fe4a:1c03/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40325 (39.3 KB)  TX bytes:34289 (33.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-4A-1C-03-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311# airmon-ng start wlan0


Interface	Chipset		Driver

wlan0			iwl3945 - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311#

```

I tried replacing "wlan0" with "wmaster0" and get the following:
```

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311# airmon-ng start wmaster0


Interface	Chipset		Driver

wlan0			iwl3945 - [phy0]

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:E6:77:7A:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=76/100  Signal level:-58 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311#

```
Which seems to somewhat work but I have to have my card in Monitor mode.  Each time I try changing it to Monitor mode this happens:
```

root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311# iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
root@a34lkj2348dsf311-desktop:/home/a34lkj2348dsf311#

```

This happens for different namings of the interface and/or says the device doesn't exist.

---

### Post by MaindotC on 2008-10-28
bump

---

### Post by MaindotC on 2008-10-28
I fiddled with it and got it to work.  For the T60 w/ 3495 card, I had to do the following:
```

ifconfig wlan0 down
ifdown wlan0
iwconfig wlan0 mode monitor
ifconfig wlan0 up

```

then I could continue w/ the tutorial as described.  I did have to use the airmon-ng command specificially for the 3495 on the aircrack-ng.org site, though.

---

