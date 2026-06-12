---
title: "Virtualbox XP won't get address after bridging.  Added commands to rc.local"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-06
I got a new linksys router with DD-WRT installed and am using static DHCP (becouse I could not find a way to give br0 a static address and I need the bridge)

I had some problems accessing my router so I disabled all bridging my deleating everything in my rc.local file except "exit 0".  I also installed moblock and uninstalled firestarter many times.  It turned out that my LAN was being blocked by moblock and the IP tables.   I solved that by adding by whitelisting my LAN.  

Anyhow,

Now after enabling bridging again, windows will not pick up an address.   

My rc.local file
> tunctl -t tap0 -u steve
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

my ifconfig
> br0       Link encap:Ethernet  HWaddr 00:04:5A:8A:44:F8  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe8a:44f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3286725 (3.1 MB)  TX bytes:1582600 (1.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:04:5A:8A:44:F8  
          inet6 addr: fe80::204:5aff:fe8a:44f8/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:10250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3408124 (3.2 MB)  TX bytes:1596358 (1.5 MB)
          Interrupt:19 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3204 (3.1 KB)  TX bytes:3204 (3.1 KB)

tap0      Link encap:Ethernet  HWaddr 00:FF:B9:73:E8:0D  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ff:b9ff:fe73:e80d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:854 errors:0 dropped:157 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:32946 (32.1 KB)  TX bytes:54726 (53.4 KB)


Any ideas?

I have had so many networking problems.  Slow, Not being able to access my local IP addresses, not being able to figure out how to assign a static address to br0, wifi radio failure (new router needed)

---

### Post by jre on 2008-01-14
Just for completeness: Mysticle solved this problem by whitelisting the forwarded traffic in MoBlock, too.

---

