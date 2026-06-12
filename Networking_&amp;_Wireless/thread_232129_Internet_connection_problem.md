---
title: "Internet connection problem"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by Stephen_A on 2006-08-08
Hi,
Just installed Ubuntu, but cannot get on line. 
I have: 
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 219.79.107.20
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 219.79.107.20
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled

And I've carefully followed all the instructions on this link:
[https://help.ubuntu.com/community/ADSLPPPoE#head-3d9e2bb5191114bc11d21704cd91a045683495ce](https://help.ubuntu.com/community/ADSLPPPoE#head-3d9e2bb5191114bc11d21704cd91a045683495ce)
To ensure the PPPoE package is intsalled. Here are the problems. 
When I typed sudo ifconfig I got the following: 

eth0      Link encap:Ethernet  HWaddr 00:0D:56:E9:F0:C3
          inet6 addr: fe80::20d:56ff:fee9:f0c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:208345 (203.4 KiB)  TX bytes:30308 (29.5 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7866 (7.6 KiB)  TX byt

So then I tried (as advised elswhere) the following: 

ping -c 5 10.0.0.2

And that resulted in this: 

stephen@sra97:~$ ping -c 5 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
From 219.79.107.20 icmp_seq=2 Destination Host Unreachable
From 219.79.107.20 icmp_seq=3 Destination Host Unreachable
From 219.79.107.20 icmp_seq=4 Destination Host Unreachable
From 219.79.107.20 icmp_seq=5 Destination Host Unreachable

--- 10.0.0.2 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4000ms
, pipe 3

As you can probably see, I know next to nothing about this. If anyone would be so kind as to shed some light on this, I'd reaaly be grateful. By the way, checked all the cables, i.e. took the cable out and plugged into another machine and that one goes sweetly on line. 

Stephen.

---

### Post by jeff_ on 2006-08-08
Well I'm not sure exactly how DSl or PPPoE works, but from your ifconfig output it looks like you don't have an ip address. I'm guessing you either need dhcp enabled or a statically assigned one. Either way you can do this from System > Administration > Networking. I'm also guessing that you need to statically assign the information your ISP provided you with which I assume is the information at the beginning of your post.

---

### Post by Stephen_A on 2006-08-08
Thanks, 
I know it seems as though I don't have an IP address, but, to the best of my knowledge I've put one in. I went to System> Administration >Networking > and entered the IP address (219.79.107.20. Then I clicked on 'Ethernet connection' (It says the  interface is active, then on 'properties' and entered the IP address in the appropriate space. I don't see how I 'don't have an IP address.' I would be grateful for any other suggestions and sorry if I'm missing something really rudimentary here.

---

### Post by Stephen_A on 2006-08-08
I've just entered: sudo mii-tool eth0 and got the result:

    eth0: negotiated 100baseTx-FD flow control, link OK

The command ifconfig eth0 confirms the driver is loaded.

---

