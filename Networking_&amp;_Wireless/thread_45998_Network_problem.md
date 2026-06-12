---
title: "Network problem"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by Andpet on 2005-07-02
I have a problem with network in ubuntu 5.04. It looks like ubuntu can not connect to the router. When i write ping 192.168.1.254, wich is the ip adress to my router, i get this message: "connect: Network is unreachable". If i write ping yahoo.com i get this message: "unknown host yahoo.com". When I write netstat -nr i get this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

I believe that it should be some numbers (ip adresses?) in there, but it is not.
If i write ifconfig iget this:
eth0      Link encap:Ethernet  HWaddr 00:0C:76:06:6E:8F
          inet6 addr: fe80::20c:76ff:fe06:6e8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:660 (660.0 b)  TX bytes:24660 (24.0 KiB)
          Interrupt:23 Base address:0xac00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1569084 (1.4 MiB)  TX bytes:1569084 (1.4 MiB)

I dont understand much of this, but i hope some of you do.

I hope some of you can help me with this problem. Please let me now if there is some more information you need.

---

### Post by spd106 on 2005-07-03
Hi, can you start by telling us what kind of nic you have. 

If it's wireless try looking in the wiki to see if it's supported.

If wired see if your router/nic are set to dhcp. You will need to have an ip address to ping the router, which the output from ifconfig says it doesn't have. If you aren't using dhcp, make sure you set the ip addresses on the same subnet. This seems obvious, but even the best of us make mistakes.

The network manager gui should provide easiest way of configuring the nic. If this doesn't work check over the /etc/network/interfaces file.

Hope this helps

---

