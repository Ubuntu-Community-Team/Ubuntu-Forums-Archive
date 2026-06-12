---
title: "Networking problem"
date: 2024-03-13
forum: Networking &amp; Wireless
---

### Post by ratooren on 2024-03-13
Hi,
I've followed all the steps in this tutorial: 
**Howto: Set up Ubuntu as a firewall/gateway router with webmin**

But whatever i try i can't get my client to connect to internet.

General setup:
1. my ubuntu server 22.04 is connected to my isp router with fixed ip on eth1
2 my ubuntu client 22.04 is connected to the 2nd nic eth2, where dhcp is serving ip to lan. In the future when it's working well my ubuntu eth2 should serve all clients in the lan
I used webmin to set up the connections.
My server is on eth1 working well and can acces internet.
DNS server is running, but i've not edited any settings as the tutorial says it should work out of the box.

Somehow i missing something because setting this up shouldn't be as hard. On my clearos box and nethserver box it worked out of the blue.

Someone could give me the correct info? Or even an other tutorial more recent? The old one is closed so there i can't put any questions anymore.

It's absolutely necessary that my eth1 and eth 2 are different subnets because the isp router is also serving a public part of my network which shouldn't see the private lan network.

So isp-router-->ubunutu-server 1 nic for itself (same subnet as isp) and 1 nic on other subnet to serve private lan-->clients with android, win, linux, ipad ..........
For further information: the ubuntu server should also be the fileserver with samba to provide the lan part with all the wished files, running Resilio Sync, Sabnzbd and what more to come.....

If further info is needed please point out which files you want to see.

Both server and client can at this be reinstalled at anytime as it's all in a test-setup until it works and only then i will continue to build it further out.
For the moment my real lan and homeserver are running on Nethserver.
The reason for wanting to use Ubuntu is it's enormous amount of available packages and a long term support. And not to forget an active community to ask for help, which is not really the case with Nethserver or Clearos.

Many thanks in advance,
Ron

---

### Post by volkswagner on 2024-03-14
There's no link to your tutorial and you have not provided any configuration information.

Did you enable IP forwarding?
Do you have NAT/Firewall rules set up?

---

### Post by ratooren on 2024-03-14
Hi, the link is [https://ubuntuforums.org/showthread.php?t=926001](https://ubuntuforums.org/showthread.php?t=926001), 
**Howto: Set up Ubuntu as a firewall/gateway router with webmin         by sammydee**
So i'm using now another dchp server then the old one mentioned in the tutorial.

 Later i've researched and followed this: [https://webmin.com/docs/modules/dhcp-server/#the-isc-dhcp-server](https://webmin.com/docs/modules/dhcp-server/#the-isc-dhcp-server)

I do have put enabling ip forward as 1.
I don&#8217; t have any nat or firewall rules at this time. Firewall isn&#8217;t started even.

Would you specify which config info you would like to see.

Working in webmin has at least created 2 yaml files automatically on the server.

On client i did not create any files. Just set the interface to dhcp in upper right corner on the desktop. The network icon keeps displaying a question mark.
By the way the server is an ubuntu desktop 22.04 with package ubuntu server installed. The dhcp server is the isc dhcp server.

---

### Post by ratooren on 2024-03-14
Below some files contents for some i think are important.The files are created automatically by webmin as i entered all the setting there.[U]

eno1.yaml file:
[/U]
network:
    ethernets:
        eno1:
            addresses: ['192.168.1.100/24']
            gateway4: 192.168.1.1
            nameservers:
                addresses: [8.8.4.4, 8.8.8.8]

[U]
enp2S0 yaml file:
[/U]
network:
    ethernets:
        enp2s0:
            addresses: ['192.168.0.1/24']
            nameservers:
                addresses: [8.8.4.4, 8.8.8.8]

[U]
DHCPD.CONF:
[/U]
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.10.255;
authoritative;
option routers 192.168.10.1;
# dhcpd.conf
#
# Sample configuration file for ISC dhcpd
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#

# option definitions common to all supported networks...
option domain-name "ron.lan";
option domain-name-servers 8.8.8.8, 8.8.4.4;

default-lease-time 600;
max-lease-time 7200;

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

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
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option subnet-mask 255.255.255.224;
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.example.com";
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
#  fixed-address fantasia.example.com;
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
# ron.lan
subnet 192.168.0.0 netmask 255.255.255.0 {
    authoritative;
    allow client-updates;
    allow unknown-clients;
    option domain-name-servers 8.8.8.8;
    option broadcast-address 192.168.0.255;
    option subnet-mask 255.255.255.0;
    option routers 192.168.0.1;
    range 192.168.0.100 192.168.0.200;
    }

All the above files are in no way edited manually.

Furthermore BIND DNS Server BIND version 9.18is installed without editing any settings.

EDITED FOR FORMAT

---

### Post by The Cog on 2024-03-14
Try editing that post and using code tags round the yaml code (Use the Go Advanced button, highlight the code and click the # button at the top of the editor). That will preserve the indenting - indenting is critical. The post as it stands is useless - just dozens of lines of syntax errors. There is no point in anyone even trying to read that.

---

### Post by ratooren on 2024-03-14
Posted new with tags i hope

yaml for eno1

```

network:
    ethernets:
        eno1:
            addresses: ['192.168.1.100/24']
            gateway4: 192.168.1.1
            nameservers:
                addresses: [8.8.4.4, 8.8.8.8]
```

yaml for enp2s0
```

network:
    ethernets:
        enp2s0:
            addresses: ['192.168.0.1/24']
            nameservers:
                addresses: [8.8.4.4, 8.8.8.8]
```

Some more info: i found that there exists also a 01-network-manager-all.yaml file which is in fact empty. Could this be interfering?
This is in this file:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

And in fact looking at the 2 auto generated files these lines are missing in that ones. Problem? Bug in the auto generate function of webmin?

---

### Post by The Cog on 2024-03-15
I know nothing about webmin except I've heard of it. Provided those config files are in the right place, netplan should be happy with them. Use the command "netplan get" to see its combined config.
Also "netplan status" to show what's configured.

As Volkwagner says:
Did you enable IP forwarding?
Do you have NAT/Firewall rules set up?

---

