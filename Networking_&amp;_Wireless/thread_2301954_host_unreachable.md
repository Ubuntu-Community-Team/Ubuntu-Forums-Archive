---
title: "host unreachable"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by jeff82 on 2015-11-06
Hi all sorry about my dumbness! my vortexbox server is unreachable its ip address is 192.168.1.255
**when i sudo arp-scan i get**
jeff@jeff-Aspire-E1-530:~$ sudo arp-scan --interface=eth0 --localnet
[sudo] password for jeff: 
Interface: eth0, datalink type: EN10MB (Ethernet)
Starting arp-scan 1.8.1 with 256 hosts ([http://www.nta-monitor.com/tools/arp-scan/](http://www.nta-monitor.com/tools/arp-scan/))
192.168.1.1    58:7f:66:59:62:03    (Unknown)
192.168.1.255    00:1e:4f:e6:a1:45    Dell Inc.

2 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.8.1: 256 hosts scanned in 1.308 seconds (195.72 hosts/sec). 2 responded

**and ipconfig**
jeff@jeff-Aspire-E1-530:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 20:1a:06:af:75:f6  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd58:7f66:5962:300:221a:6ff:feaf:75f6/64 Scope:Global
          inet6 addr: fe80::221a:6ff:feaf:75f6/64 Scope:Link
          inet6 addr: fd58:7f66:5962:300:38ae:e4a5:9a19:db22/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62598 errors:90 dropped:0 overruns:0 frame:90
          TX packets:45174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56006803 (56.0 MB)  TX bytes:5822827 (5.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:326948 (326.9 KB)  TX bytes:326948 (326.9 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:84:dc:7c:ee:b5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jeff@jeff-Aspire-E1-530:~$ sudo dhclient
RTNETLINK answers: Operation not possible due to RF-kill
RTNETLINK answers: File exists
jeff@jeff-Aspire-E1-530:~$

i also get this when i try and ping????

jeff@jeff-Aspire-E1-530:~$ ping 192.168.1.255
Do you want to ping broadcast? Then -b

---

### Post by SeijiSensei on 2015-11-06
192.168.1.255 is the "broadcast" address for the 192.168.1.0/24 network.  Both 192.168.1.0 and 192.168.1.255 cannot be assigned to hosts.  That's why you get the "broadcast" query from ping.  Give the host a different address.

---

