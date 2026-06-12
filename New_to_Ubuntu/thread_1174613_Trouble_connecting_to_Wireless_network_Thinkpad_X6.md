---
title: "Trouble connecting to Wireless network Thinkpad X61"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by conryf on 2009-05-31
I have a Thinkpad X61 running Intrepid, lspci gives this info for my wireless card:

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

I have tried both network-manager-gnome and wicd. I can connect with a ethernet cable and can change the settings on my modem router (it's a Zycel p-600, does both so I dont have to deal with pppoe) so I have tried both WPA and WEP, bith fail. 

WICD won't connect and refeeshes automatically very frequestly. But getting all the info in before a refresh, it tries to connect for few seconds and gives up. 

Network-Manager prompts me repeatedly for the WEP key but never connects. 

also here is my ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:1e:4c:9f:30:9f  
          inet6 addr: fe80::21e:4cff:fe9f:309f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60769 (60.7 KB)  TX bytes:17261 (17.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:1d:72:8a:15:af  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe8a:15af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3027405 (3.0 MB)  TX bytes:719824 (719.8 KB)
          Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-4C-9F-30-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69915 errors:0 dropped:0 overruns:0 frame:63631
          TX packets:522 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6774752 (6.7 MB)  TX bytes:42353 (42.3 KB)
          Interrupt:17 


Please help!

---

### Post by mapes12 on 2009-05-31
Here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Good luck.

Mark

---

