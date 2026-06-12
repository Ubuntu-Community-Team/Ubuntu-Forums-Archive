---
title: "Open Network Connectivity"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by all4als on 2007-07-12
Hello All,
I am a little perplexed. I have 7.4 Fiesty with everything working to satisfaction (at home only). My home network is WPA protected and I can connect on both the Ubuntu and Windoze side without hindrance. However, when I go to an open network (Insert Open Network Name Here) I can work like always on the Windoze side but on the Ubuntu side is a different story. If I hover my mouse over the Network Strength Icon is gives me conected at 76%, then if I open a browser (Opera, Firefox) I cannot view anything from any website. Therefore I am NOT connected (I think). If anyone is willing to help that would be great. I am on the open network using the bad os, and would like to be on the open network using The Linux OS. thanks again.

---

### Post by all4als on 2007-07-12
I just went back into the Ubuntu side and attempted to ping google.com, and did not have any luck. I also went into a terminal and entered the command ifconfig and did not see any ipaddress or netmask. Does this shed light on something that I have done wrong. Again thank you for your help. I also forgot to mention that I am on a dual boot laptop. So I have to go to the windoze side to access the web. My apologies if it takes some time to respond.

---

### Post by dechef on 2007-07-12
Hi , check the DNS settings , make sure that they havent changed and give us more details from the conf files ok

---

### Post by all4als on 2007-07-12
dechef thank you so much for responding. Here is my DNS config. I hope.

If I messed up the above code my dns setting in the network manager are:
24.159.64.20
24.159.64.23
24.176.125.6

As for the conf request, I am not certain where to find that. Thanks again for your help and concern

---

### Post by all4als on 2007-07-12
I am back home, and on my network without any problem. However my DNS settings are exactly the same as mentioned above. I think this is what you were asking for dechef:
I also am using a Dell Latitude D520.
```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:1D:FA:E9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:16:CE:7F:B1:B8  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe7f:b1b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9280772 (8.8 MiB)  TX bytes:637400 (622.4 KiB)
          Interrupt:17 Memory:efdfc000-efe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1640 (1.6 KiB)  TX bytes:1640 (1.6 KiB)

```

If I am displaying more than I should please let me know.

---

### Post by all4als on 2007-07-17
To resolve this I added the search domain to my DNS settings as dechef implied, and all is well.

---

### Post by all4als on 2007-08-29
However, now I am having the same issue as before. I have added the open network search domain, and I cannot connect to the web.

---

