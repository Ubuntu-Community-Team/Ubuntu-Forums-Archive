---
title: "DHCP3 server not starting - Help i am new"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by matt077 on 2009-12-04
Hi all

i am using ubuntu 9.10, i am new to ubuntu and trying to set up the dhcp3-server to give out ip address to my systems

the system as two network cards, eth0 is my main network, i am setting up dhcp on eth1 ( i edit the /etc/default/dhcp3-server with INTERFACES=”eth1&#8243;)

i have edit the /etc/dhcp3/dhcpd.conf with want i need ( i think its right!) but when i come to start the dhcp service ( by running command sudo /etc/init.d/dhcp3-server restart ) i get the error - 

matt@Ubuntu-system:~$ service dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was: 
drop_privileges: could not set group id: Operation not permitted

Can any one give me some pointers on how to do this? i have google'ed it but its confused me loads 

Thanks
Matt

---

### Post by sikander3786 on 2009-12-04
Check this out.

[http://ubuntuforums.org/showthread.php?t=1079538](http://ubuntuforums.org/showthread.php?t=1079538)

---

### Post by matt077 on 2009-12-04
thanks for the reply

i ran -
sudo tail -20 /var/log/daemon.log|grep "dhcpd"
 sudo tail -20 /var/log/syslog|grep "dhcpd"

which both of them returned no out put

When i run service dhcp3-server status, i get Status of DHCP server: dhcpd3 is not running.

I have mess around with the dhcp3-conf file but still no joy!

below is my config 

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.12.0 netmask 255.255.255.0 {
range 192.168.12.100 192.168.12.200;
option routers 192.168.12.254;
option broadcast-address 192.168.0.255;
default-lease-time 600;
max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

---

### Post by sikander3786 on 2009-12-04
I think you have messed alot with your config files. So the best way around will be to uninstall DHCP3 Server, delete all the config files and then reinstall DHCP3 Server. Step by step guide is here.

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by matt077 on 2009-12-04
if i copy that step by step guide (using that config file) would it work? just wanna prove to myself it works then i will edit to my needs

i have just uninstalled the package then re-installed it, when it tryed to start my dhcp ( at installtion) it failed

matt@Ubuntu-system:~$ sudo apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  dhcp3-server-ldap
The following NEW packages will be installed
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/373kB of archives.
After this operation, 872kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  dhcp3-server
Install these packages without verification [y/N]? Y
Preconfiguring packages ...
Selecting previously deselected package dhcp3-server.
(Reading database ... 119290 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_3.1.2-1ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up dhcp3-server (3.1.2-1ubuntu7) ...
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

output from /var/log/syslog

Dec  4 16:01:20 Ubuntu-system dhcpd: Wrote 0 leases to leases file.
Dec  4 16:01:20 Ubuntu-system dhcpd:
Dec  4 16:01:20 Ubuntu-system dhcpd: No subnet declaration for eth1 (0.0.0.0).
Dec  4 16:01:20 Ubuntu-system dhcpd: ** Ignoring requests on eth1.  If this is not what
Dec  4 16:01:20 Ubuntu-system dhcpd:    you want, please write a subnet declaration
Dec  4 16:01:20 Ubuntu-system dhcpd:    in your dhcpd.conf file for the network segment
Dec  4 16:01:20 Ubuntu-system dhcpd:    to which interface eth1 is attached. **
Dec  4 16:01:20 Ubuntu-system dhcpd:
Dec  4 16:01:20 Ubuntu-system dhcpd:
Dec  4 16:01:20 Ubuntu-system dhcpd: Not configured to listen on any interfaces!

---

### Post by sikander3786 on 2010-03-05
Sorry I was offline for the last few weeks.

Has this thread died? Have you sorted out the problem? If not I can send you an example configuration file.

Regards.

---

