---
title: "Ubuntu disconnects me from the Internet"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by thepyronaut on 2008-10-17
Basically, as soon as I start using something that creates a lot of connections (like say, a torrent), Ubuntu's wireless connection dies. At this point I stay connected to my router, but I can't access any websites, ping anything, or even access my router. If I try to disconnect then reconnect to my router, the connection eventually times out while trying Ubuntu tries to obtain an IP address.

I bought a new router, installed dd-wrt on it. I upgraded to the Intrepid beta. Nothing works. Large HTTP downloads don't seem to have any effect, just lots of connections. It does have some correlation to Ubuntu, since this problem doesn't occur on Windows XP using the same computer.

I really don't know what to do anymore. Can anyone help me?

EDIT: Here's some predictable hardware info you might want to know:
```
$ sudo lshw -c network
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:08:fe:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.123 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:94:09:51:24:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:29:A5:AE:1B   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=15/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:f9:c7:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:08:fe:67  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe08:fe67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66538402 (66.5 MB)  TX bytes:4339784 (4.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-08-FE-67-65-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by thepyronaut on 2008-10-18
Well, I believe I've fixed the problem using ndiswrapper. I tried using ndiswrapper before, but it said the hardware wasn't available. Some guesswork using lsmod lead me to believe the "ASUS WiFi-AP Solo" used some realtek driver, the one for RTL8187. So I went to the realtek website, downloaded several potential drivers, and found one who's hardware was present.

There are no apparent problems anymore. In fact the amount and strength of networks that the network manager detects has improved as well.

Somebody needs to fix the RTL8187 driver.

---

