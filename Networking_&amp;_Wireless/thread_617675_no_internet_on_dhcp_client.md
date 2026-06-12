---
title: "no internet on dhcp client"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by LRT on 2007-11-19
i have a windows client (using it as a test machine) that is being assigned an ip address via dhcp. the dhcp server (ubuntu 7.10) has two nics:

eth0: 192.168.1.101 (from router 192.168.1.1)
eth1: 192.168.17.10 (assigned statically)

the dhcp server is serving addresses from eth1 to 192.168.17.0 subnet.


**ipconfig/all on the windows client shows this:**

Windows IP Configuration



        Host Name . . . . . . . . . . . . : AAC17

        Primary Dns Suffix  . . . . . . . :

        Node Type . . . . . . . . . . . . : Broadcast

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection 2:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : D-Link DGE-530T Gigabit Ethernet Adapter

        Physical Address. . . . . . . . . : 00-15-E9-F9-F7-07

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.17.50

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.17.10

        DHCP Server . . . . . . . . . . . : 192.168.17.10

        Lease Obtained. . . . . . . . . . : Monday, November 19, 2007 3:26:37 PM

        Lease Expires . . . . . . . . . . : Monday, November 19, 2007 3:36:37 PM


**this is my dhcpd.conf on the linux machine:**

ddns-update-style none;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.17.0 netmask 255.255.255.0 {
  range 192.168.17.10 192.168.17.50;
  option routers 192.168.17.10;
}


**/etc/network/interfaces shows this:**

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1

#The secondary network interface
iface eth1 inet static
address 192.168.17.10
netmask 255.255.255.0
network 192.168.17.0
gateway 192.168.17.10


**the problem:**

everything on the windows machine seems to look OK, but i can't get any internet connection. i can't ping anything from the windows machine except for both nics on the linux machine, 192.168.1.101 (eth0) and 192.168.17.10 (eth1).

what do i need to do? i'm a bit lost.

---

