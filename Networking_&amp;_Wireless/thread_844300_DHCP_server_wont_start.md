---
title: "DHCP server wont start"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by DangerIsGo on 2008-06-29
Here: [http://www.howtoforge.com/ubuntu6.10_firewall_gateway_p9](http://www.howtoforge.com/ubuntu6.10_firewall_gateway_p9)

is stated on how to setup a DHCP server with a ShoreWall Firewall. I got the firewall working but the DHCP server refuses to start. I find this in the syslog:

Jun 29 01:19:09 firewall dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Jun 29 01:19:09 firewall dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Jun 29 01:19:09 firewall dhcpd: All rights reserved.
Jun 29 01:19:09 firewall dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 29 01:19:09 firewall dhcpd: Wrote 0 leases to leases file.
Jun 29 01:19:09 firewall dhcpd: 
Jun 29 01:19:09 firewall dhcpd: No subnet declaration for eth0 (169.254.9.73).
Jun 29 01:19:09 firewall dhcpd: ** Ignoring requests on eth0. If this is not what
Jun 29 01:19:09 firewall dhcpd: you want, please write a subnet declaration
Jun 29 01:19:09 firewall dhcpd: in your dhcpd.conf file for the network segment
Jun 29 01:19:09 firewall dhcpd: to which interface eth0 is attached. **
Jun 29 01:19:09 firewall dhcpd: 
Jun 29 01:19:09 firewall dhcpd: 
Jun 29 01:19:09 firewall dhcpd: Not configured to listen on any interfaces!

While this is my dhcpd.conf file:

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.130;
option routers 192.168.1.1;
default-lease-time 14400;
max-lease-time 14400;
option broadcast-address 192.168.1.255;
}

And this is my dhcp3-server file:

INTERFACES=eth0

Basically, eth0 is the internal NIC which will be the DHCP server to my LAN while eth1 is the NIC connected to the DSL modem, working in conjunction with PPPoEconf. So in turn, ppp0 is the WAN. Does anyone know what this message means and how would I go about fixing it? Ive searched forums and guides for the past few hours and found no fix. Thanks.

---

### Post by DangerIsGo on 2008-06-29
So I don't know what exactly I did, but after rechecking everything, I got the DCHP server to start.  Now the important part, I cannot get internet to the machines on the LAN side.  This is my dhcpd.conf file:

ddns-update-style interim;
ignore client-updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers ##.###.#.##;
option ip-forwarding on;
range dynamic-bootp 192.168.1.100 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}

while these are my policies:
#
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc net ACCEPT
loc $FW ACCEPT
loc all REJECT info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW net ACCEPT
$FW loc ACCEPT
$FW all REJECT info

#
# Policies for traffic originating from the Internet zone (net)
#
net $FW DROP info
net loc DROP info
net all DROP info

# THE FOLLOWING POLICY MUST BE LAST
all all REJECT info

#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

For laughs, I allowed everything temporarily (not now, before for a few minutes to test) and the LAN could still not get internet.  Any ideas?

---

### Post by Iowan on 2008-06-29
I'm certainly no expert, but the "range dynamic bootp" line looks unusual - my DHCP server uses a "range 192.168.1.100 192.168.1.130" line (not as an option).

---

