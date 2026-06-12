---
title: "Intel 3945 a/b/g not working"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by skhelter on 2007-06-18
I have the proper drivers for this, but apparently I still cannot get Internet access. In the terminal, I typed

```
sudo iwlist eth1 scan
```

and then subsequently entered

```
sudo iwconfig eth1 essid linksys
sudo dhclient eth1

```

to try connecting to my linksys router. However, I received the following output:

```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:a6:03:1e
Sending on   LPF/eth1/00:13:02:a6:03:1e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

```

Can anyone tell me what's wrong? I'm sorry that this post is kind of vague/rushed; I have to leave for a banquet in a few minutes, but I will be glad to clarify anything regarding my problem in like two hours.

---

### Post by p_quarles on 2007-06-18
I have the same wireless card on my laptop, and it worked without any configuration. Have you tried just using the GUI? All I had to do was right-click on the network icon, tell it the router's name and key, and it hooked up pretty quickly. 

Also, if you actually left your router's name as "linksys" it's possible that your neighbor has a router with the same name, and your card is trying to connect with the wrong network. Give it a more personalized name.

---

### Post by skhelter on 2007-06-19
I tried your right-clicking idea but it didn't work. =/ And I am certain that this router is my own...but thanks for trying to help.

hmm...if it helps, here are my outputs for:

ifconfig

```

brian@brian-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:38:05:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8452 (8.2 KiB)  TX bytes:8452 (8.2 KiB)

```

and iwconfig

```

brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7517   Missed beacon:0

sit0      no wireless extensions.

```

---

