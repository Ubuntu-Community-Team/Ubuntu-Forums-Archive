---
title: "Setting up ADSL modem"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Huji on 2008-09-21
I just installed Ubuntu 8.04 on my machine. I already have Windows XP installed.

I have an ADSL modem (Symphony brand), which I use to connect to the internet. In windows, it is configured in this way:

```


Windows IP Configuration
        Host Name . . . . . . . . . . . . : ROHANI
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-19-DB-61-83-F6
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 

PPP adapter datak:
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 213.207.xxx.xxx
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 213.207.xxx.xxx
        DNS Servers . . . . . . . . . . . : 81.91.xxx.xxx
                                            81.91.xxx.xxx
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

The IP address 213.207.xxx.xxx is given automatically, whenever I click on the network icon in "Network options" box. This IP is given to the modem, I think. Then, this modem is connected to my PC using a LAN cable, and acts like a hub. On my PC, I manually setup an IP address for my LAN card (192.168.0.101 in the above) abd voila!

Now, I tried to repeat that in Linux environment. I enabled PPPOE with the same username and password. Here is the result of ifconfig:
```


eth0      Link encap:Ethernet  HWaddr 00:19:db:61:83:f6  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe61:83f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2798 (2.7 KB)  TX bytes:6303 (6.1 KB)
          Interrupt:218 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:221880 (216.6 KB)  TX bytes:221880 (216.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:213.207.xxx.xxx  P-t-P:81.91.xxx.xxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:801 (801.0 B)  TX bytes:30 (30.0 B)

```

But, when I open Firefox, it doesn't show Google, for example. Please advise what I should do to enable the connection.

Huji

---

### Post by Huji on 2008-09-21
Ignore this! I fixed it by running pppoeconf myself. Can someone delete this question please?

---

