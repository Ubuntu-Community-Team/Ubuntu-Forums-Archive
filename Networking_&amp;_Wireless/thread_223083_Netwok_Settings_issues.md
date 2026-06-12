---
title: "Netwok Settings issues"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by siucdude on 2006-07-25
Well looks like this is a hot topic so here is some fire.  

I don't know what I did but I am having some issues with my eth0 and eth1.  I have connection but its very slow.  So I have been reading the forum and decided to go to the Network Settings and take a look.  Well its all blank.  Nothing is in the Connections.  my ifconfig is below so is other stuff.  it gets very intresting.

this is what I am posting 
1. Please post output of ifconfig eth0 (Depends on your interface number)
2. Please post output of lspci | grep Eth
3. Please post output of route -n
4. Please post output of cat /etc/resolv.conf
5. Please post output of cat /etc/network/interfaces
6. Please post output of cat /etc/dhcp3/dhclient.conf

admin@ubuntu:~$ ifconfig eth0
eth0: error fetching interface information: Device not found
admin@ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:14:85:F9:BD:66  
          inet addr:192.168.102.101  Bcast:192.168.102.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fef9:bd66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348224 (340.0 KiB)  TX bytes:75116 (73.3 KiB)
          Interrupt:233 Base address:0x8000 

admin@ubuntu:~$ lspci | grep Eth
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
admin@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.102.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.102.1   0.0.0.0         UG    0      0        0 eth1
admin@ubuntu:~$ cat /etc/resolv.conf
search gateway.2wire.net
nameserver 192.168.0.1
nameserver 192.168.1.254
admin@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface

auto eth1
iface eth1 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider
admin@ubuntu:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
admin@ubuntu:~$ 

But why would I have the Network Settings all blank should there be something I think there used to be something.

Please help.

Thanks

---

