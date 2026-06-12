---
title: "Ethernet configuration"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by pillu on 2007-01-01
I am connected to the internet through the ethernet provided by my ISP. Currently I have connected a wireless router to it and am able to connect fine. But when I connect my computer directly to the ethernet port, Ubuntu is not able to use that connection (It works just fine in Windows without having to do anything). I tried to change my default connection from wireless to ethernet in network-admin but that does not help. Ubuntu is able to get the IP correctly though when I connect. 

Could someone walk me through any configuration I need to do (I am a bit of a n00b)

Thanks a lot

---

### Post by phossal on 2007-01-01
You have cat5/6 running from your box to your router? What is the output of the following command:

```

sudo ifconfig

```

---

### Post by Hex_Mandos on 2007-01-01
I'm having a similar problem. I had to replace my ethernet card, and now I can't use the new one. (I'm connected through USB now, but it's only a temporary solution)

ifconfig gives me this:

> eth1      Link encap:Ethernet  HWaddr 00:04:75:71:D8:B1  
          inet6 addr: fe80::204:75ff:fe71:d8b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720 (720.0 b)  TX bytes:810 (810.0 b)
          Interrupt:185 

eth2      Link encap:Ethernet  HWaddr 00:14:04:AA:22:61  
          inet addr:24.232.238.61  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:4ff:feaa:2261/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9320121 (8.8 MiB)  TX bytes:1490601 (1.4 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


---

### Post by phossal on 2007-01-01
Have you tried the following (where eth0 is not the wireless)?
```

sudo ifdown eth0
sudo ifup eth0

```

Sometimes, when you're using an otherwise properly configured connection (wireless or not), you simply need to tell it to ask the router for an IP.

One way of doing that is like so:
```

sudo dhclient eth0 

```

For interacting with your networks, I strongly advise investigating the following commands, and avoiding the GUI configuration tools:
ifconfig, iwconfig, ifup, ifdown, dhclient, and dmesg. Of course, any command for manipulating your network devices is hopeless if the device isn't properly configured.

---

### Post by Hex_Mandos on 2007-01-01
So... how do I configure my network card? I'm completely clueless on the topic.

---

### Post by phossal on 2007-01-01
In your earlier post of the output to ifconfig, two eth# interfaces are appearing. Can you confirm that either is your new card? For example, if you remove the card and reboot, does one disappear?

---

### Post by Hex_Mandos on 2007-01-02
It's eth2. Now, how do I configure it to use my router?

---

### Post by pillu on 2007-01-02
Sorry for not posting for so long. I tried out the commands. This is what sudo ifconfig gives me
> eth0      Link encap:Ethernet  HWaddr 00:0F:B0:CC:76:2F
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fecc:762f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:744 (744.0 b)  TX bytes:1152 (1.1 KiB)
          Interrupt:50 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:18:DE:2C:99:86
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe2c:9986/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5078 errors:0 dropped:13 overruns:0 frame:0
          TX packets:1336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1176711 (1.1 MiB)  TX bytes:248161 (242.3 KiB)
          Interrupt:169 Base address:0x2000 Memory:d0000000-d0000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256 (256.0 b)  TX bytes:256 (256.0 b)

here eth0 is my ethernet card and eth1 is the wireless card.

Then I did ifdown and ifup with eth0. The commands work fine and seem to find the IP all right.
> anand@zorg:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:b0:cc:76:2f
Sending on   LPF/eth0/00:0f:b0:cc:76:2f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67

anand@zorg:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:b0:cc:76:2f
Sending on   LPF/eth0/00:0f:b0:cc:76:2f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 235464 seconds.

But still when I try to ping my router at 192.168.0.1 it gives me
> anand@zorg:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.103 icmp_seq=1 Destination Host Unreachable
From 192.168.0.103 icmp_seq=2 Destination Host Unreachable
From 192.168.0.103 icmp_seq=4 Destination Host Unreachable
From 192.168.0.103 icmp_seq=5 Destination Host Unreachable
From 192.168.0.103 icmp_seq=6 Destination Host Unreachable
From 192.168.0.103 icmp_seq=8 Destination Host Unreachable

This same ping is successful with the wireless. Does anyone have any idea what is going on ?

---

