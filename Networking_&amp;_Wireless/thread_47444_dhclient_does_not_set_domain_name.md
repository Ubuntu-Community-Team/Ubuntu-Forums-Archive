---
title: "dhclient does not set domain name"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by mcclen on 2005-07-08
I'm trying to setup my laptop (Thinkpad X40, 1.2 GHZ, 1.5 GB, Hoary Hedge 5.04) to get its domain suffix from the DHCP Server (D-Link DI-614+ wireless broadband router) for the built in ethernet. This appears to be working for the other PC in my home network, a Windoz desktop running XP (SP2).

Does someone know the correct procedure? Here's my configuration and details.

The contents of the dhclient.conf file (in /etc/dhcp3) have not been altered and are:

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
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


```

My /etc/resolv.conf contents are:

```

search home.net
nameserver 192.168.0.1

```


The contents of my /etc/hostname (which gets reset each reboot, networking restart?) are:

```
thinkpad
```

The contents of /etc/hosts are (this file seems out of "order"):

```

127.0.0.1 thinkpad thinkpad.home.net localhost localhost.localdomain

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet ip6-localnet
ff00::0 ip6-mcastprefix ip6-mcastprefix
ff02::1 ip6-allnodes ip6-allnodes
ff02::2 ip6-allrouters ip6-allrouters
ff02::3 ip6-allhosts ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

```

The contents of the DHCPACK packet (just the bootstrap portion, captured with ethereal on the Windoz box) are:


```

Bootstrap Protocol
    Message type: Boot Reply (2)
    Hardware type: Ethernet
    Hardware address length: 6
    Hops: 0
    Transaction ID: 0x06714d00
    Seconds elapsed: 0
    Bootp flags: 0x0000 (Unicast)
        0... .... .... .... = Broadcast flag: Unicast
        .000 0000 0000 0000 = Reserved flags: 0x0000
    Client IP address: 0.0.0.0 (0.0.0.0)
    Your (client) IP address: 192.168.0.100 (192.168.0.100)
    Next server IP address: 0.0.0.0 (0.0.0.0)
    Relay agent IP address: 0.0.0.0 (0.0.0.0)
    Client MAC address: 00:0a:e4:26:ef:b7 (Wistron_26:ef:b7)
    Server host name not given
    Boot file name not given
    Magic cookie: (OK)
    Option 53: DHCP Message Type = DHCP ACK
    Option 1: Subnet Mask = 255.255.255.0
    Option 51: IP Address Lease Time = 7 days
    Option 3: Router = 192.168.0.1
    Option 15: Domain Name = "home.net"
    Option 6: Domain Name Server = 192.168.0.1
    Option 54: Server Identifier = 192.168.0.1
    End Option
    Padding

```

My DHCP Server is setup to deliver addresses in the range 192.168.0.100 through 192.168.0.200. I am getting an IP address and the connection and DNS are otherwise "working". I did comment out the alias for ipv6 in /etc/modprobe.d/aliases  and replaced it with an "off" statement (per a previous post). This seem to have no effect. There is a wireless card on board, but it is disabled in this scenario. I have firestarter installed, but disabled. I use it mainly for the wireless card while not at home. One last note, I have VMWare 5 installed with bridging enabled.

I'm expecting the command "hostname -f" to return "thinkpad.home.net". I'm expecting the System->Administration->Networking General Tab to show hostname as "thinkpad" and domain name as "home.net". Hostname -f returns only "thinkpad", the general tab shows only thinkpad.

BTW, if I try to set the domain name in either the networking tool or in /etc/hostname it does not survive a restart.

Thoughts, suggestions?

Thanks!

---

