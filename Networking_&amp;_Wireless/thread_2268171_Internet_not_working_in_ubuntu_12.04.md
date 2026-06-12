---
title: "Internet not working in ubuntu 12.04"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by Vinoth_ on 2015-03-06
Hello Experts , 

  I am facing issue in internet , I have connected to WIFI network [ DHCP Address assigned ] where unable to surf internet. the same wifi n/w is working for other people but it not for me. 

Important Point : I also have Virtual box [ Virtual Machine ] in that i have windows 7 , Internet is working in windows using the same wifi n/w. As you guys aware that windows will get the ip from ubuntu interface. 


  a. IP Address assigned 
  b. Able to ping the gateway
  c.  nslookup [www.google.com](www.google.com) --> Not working 


Below are some of the output::::

ejknoqr@5GTFTS1:~$ ifconfig wlan0
----------------------------------
wlan0     Link encap:Ethernet  HWaddr 8c:70:5a:0a:15:00  
          inet addr:10.10.13.161  Bcast:10.10.13.255  Mask:255.255.255.0
          inet6 addr: fe80::8e70:5aff:fe0a:1500/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25934403 (25.9 MB)  TX bytes:6045414 (6.0 MB)

ejknoqr@5GTFTS1:~$ netstat -nr
--------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.10.13.1      0.0.0.0         UG        0 0          0 wlan0
10.10.13.0      0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0

ejknoqr@5GTFTS1:~$ sudo lshw -C network
--------------------------------------------
PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: d4:be:d9:20:c0:77
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:e6e00000-e6e1ffff memory:e6e80000-e6e80fff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 8c:70:5a:0a:15:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-33-generic firmware=18.168.6.1 ip=10.10.13.161 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:e6d00000-e6d01fff


Please help to fix this issue

---

### Post by TheFu on 2015-03-07
If you can ping the router, try to ping public IP addresses on the internet 8.8.8.8 is well-known.
If that works, you have a DNS issue.
If that doesn't work, you have a routing issue.

Since you can ping the router, you do not have a connection issue.

---

### Post by Bucky Ball on 2015-03-07
Welcome. In Network Manager, edit the wireless connection and make sure you have the correct DNS IPs for your ISP. Check them against the DNS addresses in the working Windows.

In fact, check everything against the working Win connection and see if you spot any anomolies.

---

### Post by Bucky Ball on 2015-03-07
Welcome. In Network Manager, edit the wireless connection and make sure you have the correct DNS IPs for your ISP. Check them against the DNS addresses in the working Windows.

In fact, check everything against the working Win connection and see if you spot any anomolies. 

PS: How are you setting the static IP on the Ubuntu install? If you have set a static IP in Network Manager, check on the router that it is not in a range that the router's DHCP server is serving IPs. That can cause issues.

---

