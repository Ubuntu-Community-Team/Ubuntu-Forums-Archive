---
title: "Help with using intel 3945 wireless adapter on HP dv9000t"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by prikhi on 2008-09-11
Hi, my Vista installation died on me recently so I thought I'd reformat and dual boot XP & Kubuntu on my HP dv9000t. Now I've got everything up and running but I can't seem to connect to my wireless network on kubuntu. I'm using the Intel 3945ABG wireless adapter.

I don't think it's a hardware problem because I can connect to the wireless network on the XP partition and I don't think it's a router compatibility issue (I have a Netgear WGT624) because I can connect to the router using an Ethernet cable while running Kubuntu. 

When I'm in Kubuntu I can right click on the network-manager and it sees my network and a few others, it begins to connect and asks me for the WEP key, I put it in (and I'm 100% sure it's correct), and the network-manager begins to connect and stop at around 57% which is Configuring IP Address. 

Any help would be appreciated, here's some diagnostics:

**iwconfig**

```
prikhi@P-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:C5:53:1C
          Bit Rate=48 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=75/100  Signal level=-59 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
**ifconfig**

```

prikhi@P-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:f7:2f:d3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x5000 Memory:da000000-da020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1000 (1000.0 B)  TX bytes:1000 (1000.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:59:31:e6
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:1080 (1.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-59-31-E6-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**/etc/network/interfaces reads:**
```
auto lo
iface lo inet loopback

```

Thanks.

---

### Post by cpetercarter on 2008-09-11
This is a well troublesome wireless card - see no end of previous posts.
 
Some people have found that installing linux-backports-modules fixes their problem. Dell Ubuntu computers which use this wireless card come with these modules installed. See [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") for a brief how-to.

---

### Post by prikhi on 2008-09-11
> **cpetercarter said:**
> This is a well troublesome wireless card - see no end of previous posts.
 
Some people have found that installing linux-backports-modules fixes their problem. Dell Ubuntu computers which use this wireless card come with these modules installed. See [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") for a brief how-to.

Hmm installing the modules didn't help put the first comment gave instructions to install wicd, which worked.

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

---

