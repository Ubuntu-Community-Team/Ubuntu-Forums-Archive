---
title: "Ubuntu 14 LTS connects to wifi hotspots but no internet"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by manuel_benitez_cor on 2016-05-20
Hi,

I am having problems connecting via wifi to a hotspot created with an android phone. It worked in the past, but after some work-around (reinstallation of lost kernel, reinstallation of NetworkManager, etc) now I cannot use it anymore.

It sees the hotspot, connects, but then there is no internet access. The hotspot works perfectly fine when connecting from the same computer under windows.

Here are the outputs from iwconfig and route -n

```

  desmond@thehatch:~$ iwconfigwwan0     no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"TheNewOtto"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: A0:39:F7:9E:02:85                                                                         
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm                                                                                                       
          Retry  long limit:7   RTS thr:off   Fragment thr:off                                                                                       
          Power Management:off                                                                                                                       
          Link Quality=70/70  Signal level=-39 dBm                                                                                                   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0                                                                                   
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0                                                                                  
                                                                                                                                                     
desmond@thehatch:~$  route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```
I've seen here the same problem in other posts but nothing worked so far.
Here it is how my /etc/network/interfaces looks like (I had to change it some time ago due to some problems at the boot, 'waiting for network configuration'):
```

# interfaces(5) file used by ifup(8) and ifdown(8)
#auto eth0
#iface eth0 inet dhcp
auto lo
iface lo inet loopback

```

Hope someone can help,
thanks!

---

