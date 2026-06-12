---
title: "Network UDP Connection Issue (PS3 &amp; Samsung PPP)"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by netterhaufen on 2008-10-18
Hello network guru's and other viewers :-),

I finally registered on the site to get some support. Before I explain my issue, here is the setup of my home network:

[Playstation 3] <---> [Ubuntu 8.04 Hardy Heron] <---> Samsung SGH U900 using USB (/dev/ttyACM0).

I manage to connect fine to the internet (HSDPA/UMTS/GPRS) using my cellphone, Ubuntu box online too, as well as Playstation 3. My problem is that UDP connections between my Playstation 3 and other remote computers fails nearly every time. I can connect fine to the Playstation 3 network etcetera, but direct UDP connections (especially in Fifa08/09 series) fail utterly. I've tried a lot, ip forwarding is enabled, masquerading and no firewall in place to block anything.

Anyway, here is a list of my settings and various outputs of the Ubuntu box, to help diagnose the issue at hand:

cat /proc/sys/net/ipv4/ip_forward
> 1

route
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

iptables -L
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

iptables -t nat -L
> Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

ping google.com
> PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=239 time=277 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=239 time=239 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=239 time=228 ms

ifconfig
> eth1      Link encap:Ethernet  HWaddr 00:18:f3:a9:9a:6f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fea9:9a6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12579977 (11.9 MB)  TX bytes:32131462 (30.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104692 (102.2 KB)  TX bytes:104692 (102.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:[removed]  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7749 errors:127 dropped:0 overruns:0 frame:0
          TX packets:7668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5616927 (5.3 MB)  TX bytes:698233 (681.8 KB)


I can post a wireshark packetlog of trying to establish connection with a PS3 user, but it really doesn't show much, except that packets are being sent from 192.168.1.1 (Playstation 3 static IP, routed through the Ubuntu box) and received, over x11 and apple-sasl ports. I made sure MTU size of Playstation 3 is set to 1500 as well, in order to avoid conflicting issues (as you see in ifconfig output MTU of ubuntu box is 1500 as well).

If anyone has an idea, it would be greatly appreciated. I hope my cellphone provider isn't blocking these ports.

Regards,

---

### Post by netterhaufen on 2008-10-18
*bump* ;)

---

