---
title: "Did a recent update break wireless?"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by coolen on 2008-08-04
Yesterday, wireless was working fine. Today, I went to Uni, and I couldn't get onto the network (I tried the A network, which is more reliable, and no go). It's not unusual, so I shrugged it off.

I got home and pulled out my laptop, went to open Firefox, and noticed that I hadn't connected yet. I checked, and the wireless network is on. None of the other networks from the building showed in Network Manager.

I tried manual configuration, and that didn't work. I also tried ethernet, but that didn't work (I don't know if that ever worked, though. I've never used it in Ubuntu).

I did a few updates yesterday, and I seem to recall one of them was regarding wireless (possibly drivers, I can't remember).

I searched the forum, but found nothing recent. My question is, did a recent update break wireless for some people?

I have the backport modules installed, in an effort to get my sound working. I think that's what was updated, but I can't be sure.

Oh, and my hardware:
Intel Wireless Wifi Link 4965 AGN, according to Device Manager (yes, I'm in Windows).

---

### Post by superprash2003 on 2008-08-04
possible.. could you post your lshw -C network output and your iwconfig output from the terminal

---

### Post by coolen on 2008-08-04
I assumed that the class for lshw -C was intel. It outputted a few things (PCI, SCSI and the like) then quit without leaving anything.

Here's iwconfig:

```
benji@sterrance:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by coolen on 2008-08-04
I got tired of XP, and went ahead and removed the backport modules.

Networks showed up as before, and I was able to connect to my home network (although I had to put the information in again).

I just wanted to confirm before I did something foolish like remove something which could be responsible for giving me sound (turns out it wasn't).

---

### Post by Statik on 2008-08-06
I now also have the same problem. Wireless just stops working. It started working yesterday, but now doesn't work again. Can't seem to get it working. Any suggestions?

Will hook a LAN cable to the laptop later and post specs if I can.

Statik

---

### Post by coolen on 2008-08-07
Do you have the backport modules installed? If so, and you don't need them for anything in particular, remove them. Solved the problem for me.

I've reported the bug. Hopefully it'll be resolved soon.

The bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/254699](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/254699)

---

### Post by Statik on 2008-08-07
No, no backport modules installed.

It looks like it might be an HP problem with CPU heat hurting other components. I have the laptop attached to the LAN now. What outputs should I post?

IWCONFIG:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

IFCONFIG:
```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:90:f9:85  
          inet addr:192.168.0.94  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe90:f985/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:415971 (406.2 KB)  TX bytes:90654 (88.5 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53792 (52.5 KB)  TX bytes:53792 (52.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:30:e9:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-30-E9-A9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Not sure where wmaster0 came from. I don't recognize it from before.

This is an HP DV2310CA laptop. Using the Broadcom B43 restricted driver.

Statik

---

### Post by giruzz on 2008-08-07
> **Statik said:**
> No, no backport modules installed.

It looks like it might be an HP problem with CPU heat hurting other components. I have the laptop attached to the LAN now. What outputs should I post?

IWCONFIG:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

IFCONFIG:
```
eth0      Link encap:Ethernet  HWaddr 00:16:d3:90:f9:85  
          inet addr:192.168.0.94  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe90:f985/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:415971 (406.2 KB)  TX bytes:90654 (88.5 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53792 (52.5 KB)  TX bytes:53792 (52.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:30:e9:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-30-E9-A9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Not sure where wmaster0 came from. I don't recognize it from before.

This is an HP DV2310CA laptop. Using the Broadcom B43 restricted driver.

Statik

Same problem here. HP Computer with MadWifi for wireless.

Lost wifi starting today. Yesterday it was working fine.

Also, the screen appears a bit 'darker' 

giruzz

---

### Post by Heide264 on 2008-08-08
I have been at my friends house for the past week and tried to get on their internet (with a mess of a failure of a result - darn you WPA2) and I assumed it was from messing with my settings. But I too now have that wmaster0 junk everywhere and can not connect via wireless or ethernet. I was thinking it might be an issue with the way wmaster is in the interfaces..

...bear with me - typing it out by hand...

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0




iface wlan0 inet static
address 192.168.1.129
netmask 255.255.255.0gateway 192.168.1.1
wireless-essid linksys

auto wlan0

iface eth0 inet static
address 192.168.1.130
netmask 255.255.255.0
gateway 192.168.1.1





And by the way, there are infact those extra line breaks there. Not quite sure what happened. Might of messed it up while trying to use network manager to connect to the WPA2 network.

---

