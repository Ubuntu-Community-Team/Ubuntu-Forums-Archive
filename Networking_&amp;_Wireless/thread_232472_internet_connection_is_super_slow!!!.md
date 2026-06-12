---
title: "internet connection is super slow!!!"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by djbwhizz on 2006-08-08
HI there... 

I just upgraded to dapper bout a month back i guess. and i just moved into this campuse which uses the university internet connection to get on the net.. in other words, it is protected by the university firewalls and stuff. 

Since i got here, my internet connection seems to be super slow. I could log on to the net, which is fine. HOwever, it is taking me ages to download a webpage.  It took me about 5mins just to open the ubuntu forum. If i do it at the campus lab, it seems pretty fast. One click and its there. What has gone wrong to my laptop? can somebody help pls....

this are the respond when i type ifconfig
ath0      Link encap:Ethernet  HWaddr 00:02:C7:FF:16:52
          inet6 addr: fe80::202:c7ff:feff:1652/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:35 dropped:0 overruns:0 frame:35
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:deba0000-debb0000

eth0      Link encap:Ethernet  HWaddr 00:30:13:1D:F8:2E
          inet addr:10.2.2.201  Bcast:10.2.7.255  Mask:255.255.248.0
          inet6 addr: fe80::230:13ff:fe1d:f82e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8755130 (8.3 MiB)  TX bytes:1089648 (1.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4930594 (4.7 MiB)  TX bytes:4930594 (4.7 MiB)

then i tried pinging the IP add (ping -c 5 10.2.2.201)
PING 10.2.2.201 (10.2.2.201) 56(84) bytes of data.
64 bytes from 10.2.2.201: icmp_seq=1 ttl=64 time=0.068 ms
64 bytes from 10.2.2.201: icmp_seq=2 ttl=64 time=0.056 ms
64 bytes from 10.2.2.201: icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from 10.2.2.201: icmp_seq=4 ttl=64 time=0.060 ms
64 bytes from 10.2.2.201: icmp_seq=5 ttl=64 time=0.056 ms

--- 10.2.2.201 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4064ms
rtt min/avg/max/mdev = 0.056/0.059/0.068/0.009 ms

when i checked on the properties of eth0, seems like there is more bytes received than sent on the activity part...

Activity:
Received: 49176 packets (9.1Mb)
Sent: 8670 packets (1.2Mb)

what is wrong? my friends comp seems to be working fine and experiencing good fast internet... 

PLs help from scratch as i am really new to all these networking stuff. Do explain all the technical terms if you are going to use it.

Thank you very much.

Help me pls....

---

### Post by x64Jimbo on 2006-08-08
You should try booting from LiveCD to see if the problem is in your hardware or software.

---

### Post by hajk on 2006-08-26
Could you show the contents of the file /etc/resolv.conf?

---

### Post by NetworkGuy on 2006-08-26
You have connectivity as shown by the pings.  You are also resolving using DNS since Firefox puls up the forum.   

I'm wondering if it isn't the IPv6 thing?  There is something in the forum on turning off IPv6.  I would try to turn it off on FireFox first.

From FireFox, type ```
about:config
```
Then in the find window type IPv6.
Double click on the network.dns.disableIPv6 to change the value from false to true.   Now try surfing and see if your performance improves.

---

