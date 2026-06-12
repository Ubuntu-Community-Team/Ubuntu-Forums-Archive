---
title: "Help Needed::Unable to connect to the network"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by orengt on 2007-12-27
I apology asking this again, last time I didn't got through it and I still have the problem. 

The last question I was asked is whether I an IP address was acquired so I don't know how to check it. The problem I see is that when running pppoeconf I got a message that my ISP cannot be found and thus I need to check my HW. However this HW should be ok since it works with Windows XP. 

My network board is: Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC and my Cable modem is Motorola SB 4200.

The following is from the system.log:
[ 73.373701] r8169: eth0: link up
[ 83.771874] eth0: no IPv6 routers present
[ 88.202027] r8169: eth0: link up
[ 90.319819] r8169: eth0: link up
[ 110.812849] eth0: no IPv6 routers present
[ 279.076120] PPP generic driver version 2.4.2
[ 279.079870] NET: Registered protocol family 24

Can someone tell what is wrong?

OrenG
______

---

### Post by icheyne on 2007-12-27
It sounds like the ethernet side of the connection is OK. If you type "ifconfig" - is there an ip address next to the eth0 section?

The problem could well be with the modem. Are all the lights on properly? Is it on standby?

---

### Post by orengt on 2007-12-27
Thanks for your quick response.

Yes I get an IP address, now that I know how to  check it, here is the ifconfig printout:

eth0      Link encap:Ethernet  HWaddr 00:19:DB:AC:F6:89   
          inet addr:172.23.188.11  Bcast:255.255.255.255  Mask:255.255.224.0 
          inet6 addr: fe80::219:dbff:feac:f689/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:13308 (12.9 KB)  TX bytes:6112 (5.9 KB) 
          Interrupt:17 Base address:0xe000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

The modem also seems to be fine, all lights are as usual and I'm righting you through it now ...

---

### Post by icheyne on 2007-12-27
> **orengt said:**
> 
The modem also seems to be fine, all lights are as usual and I'm righting you through it now ...

So you're fixed  now?

---

### Post by orengt on 2007-12-29
No because pppoeconf is still not getting through so I can't login to my ISP, it stops after scan saying that I have a problem with my HW.

---

### Post by willism on 2007-12-29
The IP address looks bogus. What does it give you under winXP? 

>inet addr:172.23.188.11 Bcast:255.255.255.255 Mask:255.255.224.0

---

### Post by orengt on 2007-12-29
That what I have in XP:

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.22.175.277
        Subnet Mask . . . . . . . . . . . : 255.255.240.0
        Default Gateway . . . . . . . . . : 172.22.160.1

PPP adapter Barak013_L2TP:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 89.0.23.199
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 89.0.23.199

---

### Post by Lusen on 2008-01-01
I think you have the wrong driver for that nic.
Your NIC RTL8168/8111 the driver r8169: eth0

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343)

---

### Post by orengt on 2008-01-01
Thanks. Could you suggest where is the best place to download r8168.ko?

---

### Post by Lusen on 2008-01-01
I have tried this
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)
but I dont get it to work, r8169 will not unload.

---

### Post by orengt on 2008-01-01
Thanks, I'll try it too an let you know how it goes.

---

### Post by orengt on 2008-01-02
Hi

I got to the same point, seems that the module was loaded (lsmod list it) but network manager is still showing 8169 :confused:

Can someone help?

Thanks

OrenG

---

