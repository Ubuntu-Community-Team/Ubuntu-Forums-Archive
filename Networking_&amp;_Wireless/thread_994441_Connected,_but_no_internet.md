---
title: "Connected, but no internet"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by mlilien on 2008-11-26
I've got a Lenovo t60p with an Atheros AR4518 wireless card.  I've had some issues with wireless since upgrading to Intrepid.  The main one being that there were some places I had previously (with 8.04 and madwifi drivers) been able to get connected to the internet where I'm no longer able to, even though I have a signal.  However, it's not that bad, and I figured that future updates to the driver would fix this.

However, I've come home for Thanksgiving break, and am unable to get on the wireless at home.  We have a WEP encrypted network, and it appears that I'm able to connect to the network, but I'm unable to browse the internet/im/etc.

iwconfig gives me this ouput for wlan0:
wlan0     IEEE 802.11abgn  ESSID:"Spiderman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:7B:FC:29   
          Bit Rate=1 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=57/100  Signal level:-58 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But I'm not knowledgeable enough to get any information from that.

Thanks in advance for any advice or fixes.

---

### Post by doas777 on 2008-11-26
I'm not seeing an IP address there. what do you get from 
```
sudo ifconfig
```

---

### Post by mlilien on 2008-11-26
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:66:dd:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17821 (17.8 KB)  TX bytes:17821 (17.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:56:d4:e5  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30940 (30.9 KB)  TX bytes:9777 (9.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-56-D4-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by doas777 on 2008-11-26
ok, you have an IP. can you ping your router? also what do you get from 
```
sudo route
```?

---

### Post by mlilien on 2008-11-26
How would I go about pinging my router?

sudo route gives me:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by doas777 on 2008-11-26
well it looks like your route is set up fine.

ok, to ping your router, open a terminal and type:
```

sudo ping 192.168.1.1

```
(you prolly don't need sudo. I do cause I locked down ping w/ bastille)

if you can ping your router, try this command:
```

nslookup www.google.com

```
if you get an error that the name is unknown, then your problem is DNS.

let us know,
franklin

---

### Post by mlilien on 2008-11-26
I was unable to ping the router.  I got this message, with seq= 1-93:
    From 192.168.1.105 icmp_seq=93 Destination Host Unreachable

and then this, until I killed the process:
ping: sendmsg: No buffer space available

---

