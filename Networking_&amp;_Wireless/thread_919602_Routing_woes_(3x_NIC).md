---
title: "Routing woes (3x NIC)"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by badfeet on 2008-09-14
Hello,

I have a 8.04 box that I'm setting up as a squid proxy/cache server
and am having some trouble getting the routing to work.  I have 3
NICs in the system (2 physical segments that route out the third to
the internet).  Squid is off right now, just trying to get the
actual routing working first.  From any computer on each of the
subnets, I can ping the subnet gateway and all of the INTERNAL
NICs in the Ubuntu box, but I cannot ping any device attached
to the subnet (192.168.1.75 can ping 172.16.0.4, but not 172.168.0.250).
Any help would be greatly appreciated.  If you need any other info
please let me know and I'll post it.



I turned IP forwarding on (net.ipv4.ip_forward = 1)and here is my
/etc/network/interfaces file:


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.4
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

auto eth1
iface eth1 inet static
address 192.168.3.4
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 172.16.0.4
netmask 255.255.0.0

--------------------------------------

netstat -nr output:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.3.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
172.16.0.0      0.0.0.0         255.255.0.0     U         0 0          0 eth2
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0

--------------------------------------

dhcp configuration:

([snip] all the default settings.  Added this at the bottom)

# ------------------- START DHCP INFO -------------------------
subnet 192.168.3.0 netmask 255.255.255.0 {
range 192.168.3.50 192.168.3.250;
default-lease-time 604800;
max-lease-time 604800;
option routers 192.168.3.4;
option subnet-mask 255.255.255.0;
option domain-name-servers 205.152.37.23, 205.152.132.23;
option nntp-server time-a.nist.gov;
option netbios-name-servers 192.168.3.5;
}
subnet 172.16.0.0 netmask 255.255.0.0 {
range 172.16.1.1 172.16.3.250;
default-lease-time 604800;
max-lease-time 604800;
option routers 172.16.0.4;
option subnet-mask 255.255.0.0;
option domain-name-servers 205.152.37.23, 205.152.132.23;
option nntp-server time-a.nist.gov;
option netbios-name-servers 192.168.3.5;
}

---

