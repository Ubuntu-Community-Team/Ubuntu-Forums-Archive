---
title: "wired network not connecting"
date: 2018-09-28
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-09-28
I apologize for this one and will mark it solved.  I found my problem.  I used nm-connection-editor and saw that I had it using the vpn.  I unchecked that and it suddenly started to work again.  Again - my apologies for wasting anybody's time!!!


I don't know what happened - it just stopped working.  Here is some stuff I did:

I replaced the cable - didn't help

ipv4 is all set to automatic
ipv6 is disabled

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

greg@greg-down:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
greg@greg-down:~$ 

greg@greg-down:~$ ifconfig -a
enp2s0: flags=-28605<UP,BROADCAST,RUNNING,MULTICAST,DYNAMIC>  mtu 1500
        ether e0:3f:49:ad:2e:0a  txqueuelen 1000  (Ethernet)
        RX packets 2037  bytes 538956 (538.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 889  bytes 107335 (107.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5049  bytes 438009 (438.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5049  bytes 438009 (438.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

from logs - a pile of these:
Time request for server 192.168.0.1 failed (101/Network is unreachable) 

I also uploaded two pictures; net1 and net2

Thank you...............

---

