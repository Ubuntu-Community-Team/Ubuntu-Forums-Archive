---
title: "dhcp server setup"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by butterman on 2006-12-09
I want to set up a dhcp server for a small all-ubuntu home network to assign a fixed IP address to two desktop computers and hand out a range of IP addresses to a laptop and various other guest computers.

I use a cable modem for internet access and my ISP requires dhcp.  Initially, I had only a single interface with a fixed IP address that ran dhcp, but I could not access the Internet with that computer. So, I now have two NIC with one dedicated to dhcp service.

Before beginning this dhcp server project, I had been connecting my computers to a router with a gateway address of 192.168.1.1 and used the router to run dhcp.  This setup was frustrating because the IP addresses keep changing.  I have disabled dhcp at the router while testing the dhcp server described here.

Q: Why do I get a "wrong network" message?  I thought eth0 and eth1 had to be on different subnets.

Below are the relevant files and error messages:

$tail -n100 /var/log/syslog
Dec  9 16:01:27 localhost dhclient: Listening on LPF/eth0/00:50:bf:1b:e4:e1
Dec  9 16:01:27 localhost dhclient: Sending on   LPF/eth0/00:50:bf:1b:e4:e1
Dec  9 16:01:27 localhost dhclient: Sending on   Socket/fallback
Dec  9 16:01:29 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec  9 16:01:29 localhost dhcpd: DHCPREQUEST for 192.168.1.101 from 00:50:bf:1b:e4:e1 via eth1: wrong network.
Dec  9 16:01:29 localhost dhcpd: DHCPNAK on 192.168.1.101 to 00:50:bf:1b:e4:e1 via eth1
Dec  9 16:01:29 localhost dhclient: DHCPNAK from 192.168.2.100
Dec  9 16:01:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec  9 16:01:29 localhost dhcpd: DHCPDISCOVER from 00:50:bf:1b:e4:e1 via eth1: network 192.168.2/24: no free leasesDec  9 16:01:33 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec  9 16:01:33 localhost dhcpd: DHCPDISCOVER from 00:50:bf:1b:e4:e1 via eth1: network 192.168.2/24: no free leases


Below is my dhcpd.conf:

option routers 192.168.1.1;

ddns-update-style none;

option domain-name "cablehead.net";

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;


# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.


subnet 192.168.1.0 netmask 255.255.255.0 {
	authoritative;
	range 192.168.1.201 192.168.1.220;
	}
# atlas
host atlas {
	hardware ethernet 00:50:BF:1B:E4:E1;
	fixed-address 192.168.1.101;
	}
# redfeather
host redfeather {
	hardware ethernet 00:30:BD:BA:2E:C4;
	fixed-address 192.168.1.102;
	}
# dhcp-interface subnet
subnet 192.168.2.0 netmask 255.255.255.0 {
	}
host dhcp-interface {
	hardware ethernet 00:08:54:50:7D:26;
	fixed-address 192.168.2.100;
	}

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BF:1B:E4:E1
          inet6 addr: fe80::250:bfff:fe1b:e4e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1304215 (1.2 MiB)  TX bytes:254690 (248.7 KiB)
          Interrupt:193 Base address:0xa800

eth1      Link encap:Ethernet  HWaddr 00:08:54:50:7D:26
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe50:7d26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41271 (40.3 KiB)  TX bytes:15517 (15.1 KiB)
          Interrupt:185 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3563162 (3.3 MiB)  TX bytes:3563162 (3.3 MiB)

~$ cat /etc/default/dhcp3-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

---

### Post by eurgain on 2006-12-10
Hi,

I do almost exactly the same thing, except that my clients are a mixture of Ubuntu and SUSE.  This is not an answer to your query, just a suggestion that I hope will be useful, so feel free to ignore it.

My initial approach was to use DHCPD.  However, I changed to DNSMasq for various reasons.

First, it is dead easy to set up as a DHCP server.
Second, it speeds up name lookups by caching names locally - you use it as your network's DNS server.
Third, it "learns" the hostnames of your transient clients (provided that their DHCP clients are configured to send that information) so you can address all clients by hostname, thereby allowing you, for example, to ssh to a laptop thhat has just joined the network without having to determine its IP address.

DNSMasq is in one of the unsupported repositories, so installation is straightforward,  and its single configuration file is well-documented.

HTH 
A

---

### Post by koenn on 2006-12-10
I don't understand your network design, maybe you could make a small drawing ? Especially the part about 2 NIC's and which NIC is connected to what ...

> So, I now have two NIC with one dedicated to dhcp service.
I don't think that's the case because your dhcp server is clearly receiving dhcp discovers/ requerst on both interfaces:

> Dec 9 16:01:29 localhost dhcpd: DHCPREQUEST for 192.168.1.101 from 00:50:bf:1b:e4:e1 via **eth1**: wrong network.
Dec 9 16:01:29 localhost dhclient: DHCPDISCOVER on **eth0** to 255.255.255.255 port 67 interval 4

The "wrong network" msg is obviously because a host from network 192.168.**1**.0 is requesting a lease via the NIC in network 192.168.**2**.0
I can't really see how that happens - make a drawing ?

---

### Post by butterman on 2006-12-11
Thanks for your replys.

Eurgain, I will check out DNSMasq.
 
Koenn, I have two NICs because, as I understand it, a single interface cannot be  both a client and a server.  I identified eth1 as the server in /etc/default/dhcp3-server as shown below (INTERFACES="eth1").

That atlas server shown in the diagram is connected to a linksys router with two cables, one for eth0 and one for eth1.  The redfeather desktop is also connected to the linksys router as is a cable modem.  Hopefully this is more clear now.

---

### Post by koenn on 2006-12-13
> Initially, I had only a single interface with a fixed IP address that ran dhcp,

That would have been correct. 
According to your drawing, you have 1 network, 192.168.1.0, gateway 192.168.1.1, but your dhcpserver is it a 2nd network (192.168.2.0)

your dhcp server is configured to either give out addresses in 192.168.1.x range via eth0, or 192.168.2.x addesses on eth1 (and in that case in can only give the reserved address to the host with the given MAC address - that would ba 'atlas' i guess). 

If, in some way, another host would get an 192.168.2.x address, it's internet access would stop because it would need to find the router - which is in a different subnet. You'd get a 'Network Unreachable' or something like that. 

In short : unplug eth1 from atlas. It's not doing anything, except ocassionally picking up a DHCPDISCOVER or DHCPREQUEST broadcast packet, and  reply with 'NAK (Not acknowledged), Wrong network'

If atlas can't get internet access, there's something wrong with atlas (network config, eg default gateway), or it is blocked by the firewall or something. Concentrate on the real problem. Having a DHCP Server That Says 'NAK' is not a sollution.

---

### Post by butterman on 2007-02-14
This solved all my problems:

[http://www.dd-wrt.com]("http://www.dd-wrt.com")

---

