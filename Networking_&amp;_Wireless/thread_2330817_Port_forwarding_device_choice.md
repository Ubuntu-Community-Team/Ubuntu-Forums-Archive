---
title: "Port forwarding device choice?"
date: 2016-07-15
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2016-07-15
The adsl router add portforwarding page  requires me to specify the device as part of the setting up of the rule. Is that a reference to the modem or the computer? The router's info page states the mac address of the router is: 8c:10:d4:cd:25:73 (shown as unknown below).

The router has a drop down menu listing all the devices referred to by Nmap below and I do not know which address to choose for my port forwarding 

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr d0:50:99:19:55:52  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d250:99ff:fe19:5552/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254350928 (254.3 MB)  TX bytes:12500398 (12.5 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:21393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5039046 (5.0 MB)  TX bytes:5039046 (5.0 MB)


robins@robins-desktop:~$ sudo nmap -sP 192.168.1.0/24

Starting Nmap 6.40 ( http://nmap.org ) at 2016-07-15 17:03 BST
Nmap scan report for Unknown (192.168.1.1)
Host is up (0.0059s latency).
MAC Address: F4:B7:E2:A9:3B:59 (Hon Hai Precision Ind. Co.)
Nmap scan report for 192.168.1.2
Host is up (0.17s latency).
MAC Address: 5C:3C:27:36:4E:9F (Samsung Electronics Co.)
Nmap scan report for 192.168.1.5
Host is up (0.18s latency).
MAC Address: 18:28:61:CD:8F:6D (AirTies Wireless Networks)
Nmap scan report for Unknown (192.168.1.8)
Host is up (0.11s latency).
MAC Address: 18:28:61:CD:8F:6D (AirTies Wireless Networks)
Nmap scan report for Unknown (192.168.1.9)
Host is up (0.0058s latency).
MAC Address: DC:D3:21:AB:09:3F (Humax Co.)
Nmap scan report for dsldevice.lan (192.168.1.254)
Host is up (0.011s latency).
MAC Address: 8C:10:D4:CD:25:73 (Unknown)
Nmap scan report for robins-desktop (192.168.1.4)
Host is up.
Nmap done: 256 IP addresses (7 hosts up) scanned in 14.48 seconds
robins@robins-desktop:~$ 

```

---

