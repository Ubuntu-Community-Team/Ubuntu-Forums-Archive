---
title: "How do I get my computer a static IP address when bridging?"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2007-12-19
I have gotten bridged networking working though this howto

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

However, I find that the ip address 192.168.1.3 (supposed to my my Desktop) is not in use on the network.

My rc.local is this:

tunctl -t tap0 -u steve
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.4 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.3 dev tap0
 arp -Ds 192.168.1.3 eth0 pub
exit 0

my ifconfig is showing this:

br0       Link encap:Ethernet  HWaddr 00:04:5A:8A:44:F8  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe8a:44f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3287274 (3.1 MB)  TX bytes:510712 (498.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:04:5A:8A:44:F8  
          inet6 addr: fe80::204:5aff:fe8a:44f8/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3348432 (3.1 MB)  TX bytes:516425 (504.3 KB)
          Interrupt:16 Base address:0xac00 

tap0      Link encap:Ethernet  HWaddr 00:FF:67:FB:26:3D  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:67ff:fefb:263d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:280 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


So is my computer connected though br0?  eth0 is then disabled and used as a conduit for bridging?  My router reports that my computers hostname, desktop, is assigned the address 192.168.1.102.  I want to assign the address myself.  How do I do this?


As a bonus question.

I find that I need to run the command "sudo chmod 0666 /dev/net/tun" in order to make the VM start.  How can I make that command run at startup?  It see that it's in rc.local, but it does not work.

---

