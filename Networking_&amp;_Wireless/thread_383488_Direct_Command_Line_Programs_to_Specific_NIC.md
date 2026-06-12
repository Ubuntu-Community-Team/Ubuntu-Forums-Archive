---
title: "Direct Command Line Programs to Specific NIC"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by timbuckner on 2007-03-13
I am pretty new to ubuntu.  I have two NICs in my laptop.  On one NIC I am going to be running iperf.  On the other I am going to run telnet and ssh.  How do I specify which NIC a command line program uses if it doesn't have an option for which NIC?

Thanks, Tim

---

### Post by lloyd_b on 2007-03-13
Basically, the interface a given program uses depends on the routing configuration, which is why those programs don't have any option for specifying interface.

For example:
eth0
   Address 192.168.0.10
   Netmask 255.255.255.0
   Gateway 192.168.0.1

eth1
   Address 192.168.1.10
   Netmask 255.255.255.0

With this configuration, you'll get 3 routes:
To the 192.168.0.x network, via eth0
To the 192.168.1.x network, via eth1
To any IP address not in the 192.168.0.x or 192.168.1.x range, to the gateway at 192.168.0.1, via eth0

So if you specify "ssh 192.168.1.32", it's in the 192.168.1.x range, so it will use eth1.   "ssh 192.168.0.17", is in the 192.168.0.range, so eth0.  "ssh 37.48.23.19" is in neither of the defined network ranges, so it goes to the default gateway at 192.168.0.1, via eth0.

The only programs that need to know the interface are those that operate at a level below normal TCP/IP messaging (for instance, WireShark, a packet capture/analysis program).  But such programs are few and far between - for the majority of network applications, you simply specify the IP address, and let the system decide which interface to use.

Lloyd B.

---

