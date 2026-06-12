---
title: "Set up dhcp for PXE Server on Ubuntu 16.04"
date: 2018-04-29
forum: Networking &amp; Wireless
---

### Post by raduoctavian on 2018-04-29
Hello guys I'm getting the following error when trying to do "sudo systemctl status isc-dhcp-server.service"

root@ubuntu:/etc/network# sudo systemctl status isc-dhcp-server.service
&#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-04-29 04:02:33 PDT; 6s ago
     Docs: man:dhcpd(8)
  Process: 2198 ExecStart=/bin/sh -ec      CONFIG_FILE=/etc/dhcp/dhcpd.conf;      if [ -f /etc/ltsp/dhcpd.conf ]; then CONFIG_FILE=/etc/ltsp/dhcpd.conf; fi;      [ -e /var/lib/dhcp/dhcpd.leases ] || touch
 Main PID: 2198 (code=exited, status=1/FAILURE)


Apr 29 04:02:33 ubuntu sh[2198]: If you think you have received this message due to a bug rather
Apr 29 04:02:33 ubuntu dhcpd[2198]: than a configuration issue please read the section on submitting
Apr 29 04:02:33 ubuntu sh[2198]: than a configuration issue please read the section on submitting
Apr 29 04:02:33 ubuntu sh[2198]: bugs on either our web page at [www.isc.org](www.isc.org) or in the README file
Apr 29 04:02:33 ubuntu sh[2198]: before submitting a bug.  These pages explain the proper
Apr 29 04:02:33 ubuntu sh[2198]: process and the information we find helpful for debugging..
Apr 29 04:02:33 ubuntu sh[2198]: exiting.
Apr 29 04:02:33 ubuntu systemd[1]: isc-dhcp-server.service: Main process exited, code=exited, status=1/FAILURE
Apr 29 04:02:33 ubuntu systemd[1]: isc-dhcp-server.service: Unit entered failed state.
Apr 29 04:02:33 ubuntu systemd[1]: isc-dhcp-server.service: Failed with result 'exit-code'.

Below my /etc/dhcp/dhcpd.conf:

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;


# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.


subnet 10.152.187.0 netmask 255.255.255.0 {
}


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
 subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.150 192.168.1.200;
 option domain-name-servers 8.8.8.8 8.4.4.4;
 option domain-name "local";
 option subnet-mask 255.255.255.0;
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
}


# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.


#host ubuntu-client {
#hardware ethernet 00:0c:29:b9:9a:46;
#fixed-address 192.168.1.160;
#}


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





I'm trying to follow [https://www.ostechnix.com/install-dhcp-server-in-ubuntu-16-04/](https://www.ostechnix.com/install-dhcp-server-in-ubuntu-16-04/) and [https://www.ostechnix.com/how-to-install-pxe-server-on-ubuntu-16-04/](https://www.ostechnix.com/how-to-install-pxe-server-on-ubuntu-16-04/)

I've been struggling for the past 8h.

Please help.

Radu

---

