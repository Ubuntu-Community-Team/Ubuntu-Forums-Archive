---
title: "Ubuntu server 12.04 Networking - Can ssh to server but cannot ping from server"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by mike106 on 2013-09-26
All,

I have Ubuntu server on some x86 hardware, and the networking is behaving strangely.

Router 192.168.69.1 / 24 - Serving DHCP
Server 192.168.69.69 / 24 - Serving https (80, 8080, 32400), ssh, NFS
Client 192.168.69.108 / 24 - Ubuntu desktop version

From the client I can get to the internet using Google's DNS (8.8.8.8).

Server used to be DNS, but I uninstalled bind9.  Server also does NFS, Plex media, http (port 80) and Tomcat (8080).

From the client (any client, as well), I can ssh to the server, ping the server (and router) and can access all ports and services (NFS, Plex, http and tomcat http).  I can login to 443 on the router, too, and it's only serving https.

From the server, I can ping the client.

However, I cannot ping the router or get to the internet.  I have set the resolv.conf on the server to use google (8.8.8.8) just like the client, and DNS does not work.

The only entries in the host server's hosts files include loopback and the local host.

The routing table on the server looks correct, as do the network interfaces.

I cannot, for the life of me, figure out why the server will not talk to anything outside of the network and gives me a no route to host for the router ONLY.  I can ping the router from the client just fine, and I can ping the client from the server just fine.

Any suggestions?

---

### Post by 7182818 on 2013-09-26
Can you post the output of the 'route' command from the server?  Also, the output of 'ifconfig'?

---

### Post by mike106 on 2013-09-27
root@******:~# ifconfig
br0       Link encap:Ethernet  HWaddr 00:40:f4:2c:51:e6
          inet addr:192.168.69.69  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe2c:51e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4938060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3795798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5773254355 (5.7 GB)  TX bytes:795218036 (795.2 MB)


eth0      Link encap:Ethernet  HWaddr 00:40:f4:2c:51:e6
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4945566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3814128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5844582595 (5.8 GB)  TX bytes:796398351 (796.3 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:135885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:384135101 (384.1 MB)  TX bytes:384135101 (384.1 MB)


root@******:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.69.1    0.0.0.0         UG    0      0        0 br0
192.168.69.0    *               255.255.255.0   U     0      0        0 br0

---

### Post by 7182818 on 2013-09-27
I'm not too familiar with the bridge interface setup, but maybe the issue lies there.  For one thing, it seems odd that if a bridge interface consists of just one interface that the RX and TX byte counts aren't the same as the one interface.  Maybe try tearing down the bridge interface and seeing if you can just get things working by configuring eth0 directly.  The page [here]("https://help.ubuntu.com/community/NetworkConnectionBridge") appears to have some good info on configuring bridge interfaces, with information on how to delete them at the bottom.

---

