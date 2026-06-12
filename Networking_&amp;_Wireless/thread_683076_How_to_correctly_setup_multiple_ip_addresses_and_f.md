---
title: "How to correctly setup multiple ip addresses and force outgoing ip address?"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by quaoar on 2008-01-30
We have a server acting as web-server running Ubuntu LAMP server which hosts several domains. 
A new requirement for some of those domains is that they have to use SSL encryption. For this to work, we have to add several more ip addresses to our server. 
From what I understand, this can be done without adding more NICs. We just configure some aliases for eth0.

This was my initial try for enabling multiple ip addresses for one NIC:
Changing /etc/network/interfaces to look like this (using local IPs for this example):
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.2.149
        netmask 255.255.255.0
        gateway 192.168.2.1

auto eth0:1
iface eth0:1 inet static
        address 192.168.2.144
        netmask 255.255.255.0
        gateway 192.168.2.1

auto eth0:2
iface eth0:2 inet static
        address 192.168.2.145
        netmask 255.255.255.0
        gateway 192.168.2.1

```

This seemed to work, until we discovered a problem with outgoing traffic, like ftp/ssh, reporting their host to be 192.168.2.144 or 192.168.2.145, when they should always be 192.168.2.149 (the main IP). This seemed to be pretty random. Most of the time the traffic is coming from .149, but from time to time traffic is coming from .144 or .145. 
Traffic from any other IP than .149 creates problems since there are several firewalls at different locations which are only configured to accept traffic from .149.

Have be missed something important in interfaces-file which should be configured?

Is there some (easy) way to force all outbound traffic, or some specific outbound traffic like ftp/ssh, to always "come from" IP 192.168.2.149?


Any help much appreciated!

---

### Post by lungdart on 2008-01-31
A quick google search for 'linux how to force outbound traffic' yeilded this result

[http://www.jroller.com/agileanswers/entry/specify_source_ip_address_in](http://www.jroller.com/agileanswers/entry/specify_source_ip_address_in)

The following is the good information which seems to be exactly what your looking for.

---

Specify source IP address in outbound traffic using Linux

There are a number of reasons you might want to specify the IP from which your outbound traffic appears to originate. It is common practice to setup IP aliases on a single NIC but by default the primary IP assigned to the NIC will be used as the source IP for all traffic outbound through that NIC.

The route command provides an easy solution since it accepts a NIC alias as a normal device:

route add -host 192.168.2.105 dev eth0:1

The above command will configure your Linux box to use the IP alias bound to eth0:1 as the source for all traffic destined for host 192.168.2.105

----

So the old ```
route add -host 192.168.0.1/24 dev eth0
``` Should route all traffic through eth0 to any target within the 192.168.0.x octet. use what ever method you want for managing your destination IP's. you can drop the add -host IP to have all traffic to all sources go through eth0 and not an alias.

---

