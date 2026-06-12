---
title: "Broadcom 4306 exists... but not the IP"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by pteri498 on 2007-03-10
I'm using a D-Link DI-624 router with my Broadcom 4306 card. I followed the following tutorial:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

I've got the card set up, and input the WEP key. Everything looks good, and it connected, but I can find no IP information. I ran ifconfig to take a look at what I have:

Note: eth0 is my wireless; eth1 is my wired connection (I'll work on the naming later, for now I just want to connect)

cedric@cedders:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:4B:4E:CC:9D  
          inet6 addr: fe80::290:4bff:fe4e:cc9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59873 (58.4 KiB)  TX bytes:15847 (15.4 KiB)
          Interrupt:255 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:0F:20:25:88:2C  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe25:882c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:490170 (478.6 KiB)  TX bytes:90973 (88.8 KiB)
          Interrupt:10 Base address:0xe000


How do I get my wireless to mimic what eth1 is already doing correctly?

---

### Post by chili555 on 2007-03-10
Is it possible you are looking for an IP address from your wireless (eth0) when you already have one from your wired (eth1)? I am not sure, even with considerable modification, you can get two IPs from two different interfaces at the same time.

I suggest sudo ifdown eth1, disconnect the wire, followed by sudo dhclient eth0. 

Let us know.

---

