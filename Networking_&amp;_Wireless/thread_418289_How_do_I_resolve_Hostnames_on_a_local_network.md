---
title: "How do I resolve Hostnames on a local network?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by safehazing on 2007-04-22
I have an ubuntu Edgy server acting as Samba server and to ssh into it I need to give the command ssh username@192.168.2.2 this works fine but i would rather be able to use ssh username@servername how do i do this?

the server is also a dhcp server and i have set up dnsmasq on it which works fine for external websites but will not resolve the hostnames of machines on my network. All of the machines on my network are reachable by their IP address but not by their hostnames - what should I change to get this to work? Is this something i need to alter on dnsmasq.conf or am i looking in the wrong place? 

I have searched google and seen references to winbind but nothing that confirms this will solve my problem. 

Any idea would be appreciated.

Thanks.

---

### Post by bloodniece on 2007-04-22
Here is how I handle hostnames on a LAN.

```
sudo nano /etc/hosts
```

Put your hostnames to IP assignments right before this line:

# The following lines are desirable for IPv6 capable hosts

Example:
```
192.168.1.123   mailserv
192.168.1.125 fileserv
```

Hit ctrl+o to save, ctrl+x to exit
Also, it never hurts to backup the hosts file before fussing with it.

```
sudo cp /etc/hosts  /etc/hosts.backup
```

---

### Post by RandomJoe on 2007-04-22
I use dnsmasq as well.  Do you have it set up to be the DHCP server, or are you using a separate DHCP server?  I use dnsmasq for DHCP, and it works just fine to resolve local hostnames.  The only "problem" is when I use my work laptop, which has a different domain hardcoded in, at which point I have to use FQDNs to get to internal machines.  But that's not a big deal.

Here is my dnsmasq config (well, the  uncommented lines.  It's a long file!).  I have two internal subnets - wireless is separate from wired - and a handful of DHCP clients that get fixed IPs based off MAC / reported hostname.  In identifying the adapters to use, I used 'except-interface' to be sure it excluded the Internet-facing one.  And I use a different file from 'resolv.conf' because I have the server set up to use itself for DNS (resolv.conf has its own IP in it) so dnsmasq gets the real DNS IPs from the 'resolv.conf.cox' file.

For machines (like your server) that are fixed IPs, you will have to add them to /etc/hosts and dnsmasq will pick them up there, as shown above.

Hope this helps!

```

# Configuration file for dnsmasq.
#
# Never forward plain names (without a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv

filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
resolv-file=/etc/resolv.conf.cox

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/
local=/n5usr.ampr.org/

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=
# Or you can specify which interface _not_ to listen on
except-interface=eth0

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk
domain=n5usr.ampr.org

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
#dhcp-range=192.168.0.50,192.168.0.150,12h
dhcp-range=lan,192.168.144.50,192.168.144.99,1h
dhcp-range=wlan,192.168.120.50,192.168.120.99,1h

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60
dhcp-host=00:11:11:97:D8:B9,192.168.144.3,christine
dhcp-host=00:40:05:4A:CD:E0,192.168.144.10,printer,infinite
dhcp-host=00:0D:88:73:49:CE,192.168.144.11,back
dhcp-host=00:0D:88:73:49:CD,192.168.144.12,front
dhcp-host=00:0D:88:73:5C:04,192.168.144.13,drive


# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
dhcp-option=lan,42,192.168.144.1
dhcp-option=wlan,42,192.168.120.1

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses the same
# the same option, and this URL provides more information:
# http://www.isc.org/index.pl?/sw/dhcp/authoritative.php
dhcp-authoritative


```

---

### Post by deadguy on 2008-06-27
I have the same problem as the original post.  The really weird bit is that I can dig my hostnames, and get a resolution from dnsmasq.  But when I try to ping, I get unknown host error.

---

### Post by unutbu on 2008-06-27
I may not know enough to help you, but please post
```

cat /etc/resolv.conf
```

---

