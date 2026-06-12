---
title: "Network Bridge"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by chrisdeeley on 2007-10-07
I've just been working on linking my PC, Ubuntu Server and my Router together using a network bridge.

The idea was to link the PC to the router through my server, ie create a bridge on the server between wlan0 and eth0.

**router** --- (wlan0) ---> **server** --- (eth0) ---> **PC**

 I do this using the following commands in /etc/rc.local

ifconfig wlan0 0.0.0.0
ifconfig eth0 0.0.0.0
brctl addbr bridge1
brctl addif bridge1 eth0
brctl addif bridge1 wlan0
iwconfig wlan0 essid NETGEAR enc xxxxxxxx
ifconfig bridge1 up
dhclient bridge1

The problem i'm having is that my server can ping both the PC and the router because it hosts the bridge, but my PC cannot talk to the router or vice versa.

How do I get the server to 'pass on' connections from the PC to the router?

---

### Post by kevdog on 2007-10-07
Whats the route statement on both the bridge and pc??

route -n

---

### Post by chrisdeeley on 2007-10-07
On the bridge :

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 bridge1
0.0.0.0         10.0.0.100      0.0.0.0         UG    0      0        0 bridge1


The PC is running windows XP so no route statement

---

### Post by kevdog on 2007-10-07
Is this the correct gateway IP address??

10.0.0.100

---

### Post by chrisdeeley on 2007-10-07
yes 10.0.0.100 is the router

---

### Post by kevdog on 2007-10-07
Ok I take it that from the bridge computer you can connect out through the router.

What is the gateway of the other computer??  And is the PC being assigned an IP address through DHCP by the router??  What does ipconfig /all (I think thats the command) say??

Do you know the IP addresses of the router, bridge, PC?

---

### Post by chrisdeeley on 2007-10-07
Yes the bridge can connect to the router and the PC.

The router assigns an address by DHCP to the bridge, the IP address is 10.0.0.1, and I have manually configured the IP address on the PC (10.0.0.21), and the netmasks are the same. I have tried chaging the gateway on the PC to both the router and bridge IP address but it still can't connect through the bridge, to the router.

ipconfig /all , on the PC is as follows 

Windows IP Configuration

        Host Name . . . . . . . . . . . . : hppavilion
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce MCP Networking Control
ler
        Physical Address. . . . . . . . . : 00-0E-A6-60-6E-3D
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 10.0.0.21
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        IP Address. . . . . . . . . . . . : fe80::20e:a6ff:fe60:6e3d%7
        Default Gateway . . . . . . . . . : 10.0.0.100
        DNS Servers . . . . . . . . . . . : 10.0.0.100
                                            fec0:0:0:ffff::1%4
                                            fec0:0:0:ffff::2%4
                                            fec0:0:0:ffff::3%4

---

