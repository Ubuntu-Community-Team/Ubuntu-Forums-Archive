---
title: "Correct configuration of VLAN for second network"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by janck on 2015-02-18
I have a problem with setting up VLAN for correctly working internet connection through one cable. My ISP have Data and Video connection which are basically separated:


[LIST]
[*]Data is used for normal internet activities such as browsing on web and local connection between computers
[*]Video is used for IPTV and archived content of TV channels (timeshift)
[/LIST]
If I connect my computer to data with one cable on one interface (eth0) the network is located on 192.168.1.0 /24. If I disconnect data cable and connect my computer to video with the same cable on same interface the network is located on 10.10.8.0 /22. In both cases there is running dhcp server and I get different DNS IPs as well. But the thing is that my ISP also provides trunk connection which split data connection to VLAN ID 0 and video connection to VLAN ID 100.

Here is some info about my network when connected only to Data port:

```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10056386 (10.0 MB)  TX bytes:32561 (32.5 KB)

```

And also for network when connected only to Video port:

```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.10.10.29  Bcast:10.10.11.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9754438 (9.7 MB)  TX bytes:14789 (14.7 KB)

```

Because I would like to access to both "types" of connection, I installed vlan package (I'm using Xubuntu 14.04) and tried to somehow connected both parts. So there is my config from */etc/network/interfaces*:
```
auto lo
iface lo inet loopback

auto eth0 eth0.100

allow-hotplug eth0
iface eth0 inet dhcp
 mtu 1492

allow-hotplug eth0.100
iface eth0.100 inet static
 address 10.10.10.29
 netmask 255.255.252.0
 gateway 10.10.8.1
 dns-nameservers 10.240.93.5 10.240.93.6
 dns-search isp-domain.com
 vlan_raw_device eth0
 up route add -net 10.240.0.0 netmask 255.255.0.0 dev eth0.100
 up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0.100
```

I'm using static configuration for eth0.100 because I can't get DHCP working for VLAN 100. Internet connection (eth0) is working without the problem and I get IP from DHCP server (192.168.1.12). The problem is with video connection (eth0.100) because I have static IP and I'm able to access multicast streams (IPTV), but I can't access to DNS (10.240.93.5 and 10.240.93.6). I need DNS because I only have links pointing to archive content (timeshift) and there are different domains which needs to be resolved. I also tried to enter IP instead of domain for content archive which I got previously when my computer was connected only to video, but the problem remains, I'm not able to watch anything from archive. If I try to lookup for IP from DNS server:

```
johnny@home:~$ nslookup
> server 10.240.93.5
Default server: 10.240.93.5
Address: 10.240.93.5#53
> nslookup archive.isp-domain.com
;; connection timed out; no servers could be reached
> 
```

In the case above, *archive.isp-domain.com* is pointing to HTTP server where the content is stored. This domain is accessible only from local network 10.10.8.0 /22. If I ran the same lookup when I'm connected only to video port, I get back correct IP address which is pointing to content archive where I'm able to watch videos.

Because I know only the basics of networking and some theoretical part of VLANs, I don't know what could be wrong. I would really appreciate any help. Thanks!

---

