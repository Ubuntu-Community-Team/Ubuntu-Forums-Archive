---
title: "Wireless and wired given same interface?"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by dnairb on 2008-05-02
**System -> Administration -> Network Tools -> eth0 interface -> configure** gives the following alert:

> **The interface does not exist**
Check that it is correctly typed and that it is correctly supported by your system.

I also noticed that the interface statistics on this tab shows thousands of reception errors, even though the network is active and working OK.

So I tried a few terminal commands:

**sudo lshw -C network** gives:
 
```
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:17:3f:fd:f1:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11b/g
```


**iwconfig** gives:

```
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"WNow"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:17:3F:5B:B1:9F   
          Bit Rate=24 Mb/s   
          Link Quality=100/100  Signal level=57/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


**ifconfig** gives:

```
eth0      Link encap:Ethernet  HWaddr 00:17:3f:fd:f1:c0  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2440 errors:25583 dropped:78 overruns:0 frame:25516
          TX packets:4219 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2161088 (2.0 MB)  TX bytes:385947 (376.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2085 (2.0 KB)  TX bytes:2085 (2.0 KB)
```


This seems that Ubuntu has eth0 as both a wired **and** a wireless interface.

I have a Lan port on my box, but have disabled it in BIOS as I don't use it. I have a wireless adapter (Belkin F5D7050, version 4 using the open zd1211 driver) that worked perfectly in Gutsy and other than this problem works OK in Hardy.

Any ideas as to what is going on?

**EDIT: The above occurs on a fresh-install of Hardy, and running from the Live CD, with or without LAN enabled in BIOS

---

### Post by FrosT59 on 2008-05-02
Same problem here


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"20b7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0E:9B:4E:1C:BB   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality=86/100  Signal level=-45 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

