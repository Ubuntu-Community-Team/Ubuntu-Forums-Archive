---
title: "Server config problems"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by SupremeOverlord on 2008-08-27
I need to set up a network with three hosts: a desktop running Ubuntu, a laptop running Vista, and an Ethernet printer.  I have a switch but not a router.  My Ubuntu desktop has two Ethernet interfaces so my plan was to set up that computer as a router.  I installed dhcp3-server and configured in like so:

> # Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server.
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell [http://code.seanodonnell.com](http://code.seanodonnell.com)
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc;

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
#option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses
option domain-name-servers 192.168.1.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS
#

# assign the defaul lease time (seconds)
#default-lease-time 600000000;

# assign the max lease time (seconds)
#max-lease-time 720000000;

# eth1 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.200;
  option domain-name "cpk.umbc.net";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

However when I try to start the service I it fails:

> jake@ubuntu:~$ sudo /etc/init.d/dhcp3-server restart
[sudo] password for jake: 
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                           [fail] 
jake@ubuntu:~$ 

I have also run into problems configuring my interfaces.  Currently eth0 is dhcp and eth1 is not configured.  It seems that if I configure eth1 than my internet connection fails.  What I need is for all internal traffic to go through eth1, which should be statically configured and for all output traffic to be forwarded to eth0 and then to the internet.

---

### Post by Iowan on 2008-08-27
Failure is probably due to the interfaces problem - eth1 isn't in the subnet.
Can you post the **/etc/network/interfaces** file and results of **ifconfig**? There should be an "auto" line for both eth0 and eth1.  Network manager may not let you do it, but you can edit it into the file yourself (remember to use **sudo** - or **gksudo** for graphics editor).

[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a good document on ICS.

---

### Post by SupremeOverlord on 2008-08-27
Here is my **/etc/network/interfaces**:

> auto lo
iface lo inet loopback

iface eth1 inet dhcp
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

Here is my **ifconfig**:

> jake@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:4e:d4:3e  
          inet addr:10.1.5.138  Bcast:10.1.5.139  Mask:255.255.255.252
          inet6 addr: fe80::21a:92ff:fe4e:d43e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:711011 (694.3 KB)  TX bytes:277852 (271.3 KB)
          Interrupt:248 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:4e:df:28  
          inet6 addr: fe80::21a:92ff:fe4e:df28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17106 (16.7 KB)
          Interrupt:249 Base address:0xc000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:92:4e:df:28  
          inet addr:169.254.6.109  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:249 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:188428 (184.0 KB)  TX bytes:188428 (184.0 KB)

jake@ubuntu:~$ 


---

### Post by SupremeOverlord on 2008-08-27
I changed the **/etc/network/interfaces** file to:

> auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth0 eth1

This seemed to get my interfaces working.  **ifconfig** showed them both configured and I even got the dhcp3-server to start, but then suddenly my internet stoped!  I check **ifconfig**:

> eth0      Link encap:Ethernet  HWaddr 00:1a:92:4e:d4:3e  
          inet addr:10.1.5.138  Bcast:10.1.5.139  Mask:255.255.255.252
          inet6 addr: fe80::21a:92ff:fe4e:d43e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57264552 (54.6 MB)  TX bytes:3738407 (3.5 MB)
          Interrupt:248 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:4e:df:28  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe4e:df28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:51955 (50.7 KB)
          Interrupt:249 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194838 (190.2 KB)  TX bytes:194838 (190.2 KB)

Why would eth1 suddenly change addresses?

---

### Post by Iowan on 2008-08-27
I suspect it's no coincidence that eth1 got an address at the top of the DHCP range -  DHCP3-server seems to start with the high address and work down. The question would be: Why is eth1 getting a DHCP address (from itself???)

Just a thought - if that's a "standard" desktop, check under network settings to see if Network Manager may think eth1 gets DHCP address (it *shouldn't*)

---

### Post by SupremeOverlord on 2008-08-27
I checked in Network Settings and it shows one as a dhcp and the other as a static address 192.168.1.1, which is exactly what I want.  Everything seems to be working fine now; maybe this was a one time bug.

---

### Post by Iowan on 2008-08-27
Keep your fingers crossed!  It's possible that "we" should have done a **/etc/init.d/networking restart**.

---

