---
title: "dhcp3-server fails to start"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by peddy on 2008-09-30
Could someone please help me getting dhcp3-server running?

I get this error when running it: 

[code] * Starting DHCP server dhcpd3                                           [[COLOR="Red"]fail[/COLOR]] 

Thanks

---

### Post by MrFSL on 2008-09-30
Check out the contents of your logs. It can really give good information.

---

### Post by peddy on 2008-09-30
Nothing in the logs except some references to the vmware dhcpd server. Perhaps this could be interfering? Are there any other logs I can check?

```
~$ dmesg | grep -i dhcp
[   98.575723] /dev/vmnet: open called by PID 10765 (vmnet-dhcpd)
[   98.675631] /dev/vmnet: open called by PID 10847 (vmnet-dhcpd)
```

Thanks for your help.

---

### Post by superprash2003 on 2008-09-30
post contents of the dhcpd3.conf file

---

### Post by peddy on 2008-09-30
```

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
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

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
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
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
#### BLUEMAN AUTOMAGIC SUBNET ####
# Everything inside this section is destroyed after config change
subnet 192.168.20.0 netmask 255.255.255.0 {
				option domain-name-servers 192.168.1.1;
				option subnet-mask 255.255.255.0;
				option routers 192.168.20.1;
				range 192.168.20.2 192.168.20.254;
				}
#### END BLUEMAN AUTOMAGIC SUBNET ####
```

Thanks

EDIT: dhcp3-server should still work if my router uses DHCP, right?

---

### Post by MrFSL on 2008-10-01
Competing DHCP servers on the same network can cause problems.

---

### Post by peddy on 2008-10-01
if I turn off the router's DHCP, dhcp3-server still fails to start.

---

### Post by peddy on 2008-10-01
Aha, I found a new syslog! 

```
Oct  1 20:58:49 moonshine dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Oct  1 20:58:49 moonshine dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Oct  1 20:58:49 moonshine dhcpd: All rights reserved.
Oct  1 20:58:49 moonshine dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Oct  1 20:58:49 moonshine dhcpd: Wrote 0 leases to leases file.
Oct  1 20:58:49 moonshine dhcpd: 
Oct  1 20:58:49 moonshine dhcpd: No subnet declaration for eth0 (0.0.0.0).
Oct  1 20:58:49 moonshine dhcpd: ** Ignoring requests on eth0.  If this is not what
Oct  1 20:58:49 moonshine dhcpd:    you want, please write a subnet declaration
Oct  1 20:58:49 moonshine dhcpd:    in your dhcpd.conf file for the network segment
Oct  1 20:58:49 moonshine dhcpd:    to which interface eth0 is attached. **
Oct  1 20:58:49 moonshine dhcpd: 
Oct  1 20:58:49 moonshine dhcpd: 
Oct  1 20:58:49 moonshine dhcpd: Not configured to listen on any interfaces!

```

How do I give eth0 a subnet declaration? when I change it to wlan0 (because I use wifi), the error stays the same.

Thanks

---

### Post by peddy on 2008-10-03
[img]http://www.parrottimes.com/forums/images/smilies/bump.gif[/img]

---

### Post by Iowan on 2008-10-03
What is IP address for eth0 - 192.168.20.X?

---

### Post by peddy on 2008-10-03
No, it's 192.168.1.2; how do I change the config to reflect this?

Thanks

---

### Post by Iowan on 2008-10-03
```
#### BLUEMAN AUTOMAGIC SUBNET ####
# Everything inside this section is destroyed after config change
subnet 192.168.20.0 netmask 255.255.255.0 {
				option domain-name-servers 192.168.1.1;
				option subnet-mask 255.255.255.0;
				option routers 192.168.20.1;
				range 192.168.20.2 192.168.20.254;
				}
#### END BLUEMAN AUTOMAGIC SUBNET ####
```This appears to be the active portion of your config file - the rest is commented out.  Change the subnet to 192.168.1.0. The range should also be in the 192.168.1.x subnet (do you need 253 clients?) Presumably, the router should also have a "local" address.
If your eth0 is 192.168.1.2, you won't want to include that address in the range.  I gave myself the first 10 addresses for routers, servers, printers, etc - my range starts at x.x.x.11

One other thing I thought of... is the 192.168.1.2 via DHCP or static?  If DHCP, it may be difficult to keep the DHCP server's address out of it's own assignment range... which is to say, the DHCP server's eth0 should probably be static (or static lease).

---

### Post by peddy on 2008-10-03
OK, I changed it to this:

```
#### BLUEMAN AUTOMAGIC SUBNET ####
# Everything inside this section is destroyed after config change
subnet 192.168.1.0 netmask 255.255.255.0 {
				option domain-name-servers 192.168.1.1;
				option subnet-mask 255.255.255.0;
				option routers 192.168.1.1;
				range 192.168.1.2 192.168.1.5;
				}
#### END BLUEMAN AUTOMAGIC SUBNET ####
```

Is this correct? When start DHCP it still says 'fail'. I don't think the problem is with the config though; unless DHCP fails to stop or start when there is a broken conf file.  When I set the sample conf, or any other one for that matter, dhcp3-server still fails to stop or start. I have purged and reinstalled. Any other suggestions?

Thanks for your help so far [img]http://img246.imageshack.us/img246/8399/thumbsup4kk.gif[/img]

---

### Post by Iowan on 2008-10-03
> **peddy said:**
>  I don't think the problem is with the config though; unless DHCP fails to stop or start when there is a broken conf file. A bad config file is the primary reason most services (DHCP, Samba, etc) fail to start. Maybe "we" missed something higher up...  If necessary, I'll edit a copy of mine and post it.

OK, this *might* cause problems:```
# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

```In my file, I repeated the DNS address (for you, it'd be 192.168.1.1) Doesn't seem necessary, but works for me.  I have my "workgroup" name as my domain name.  Commenting them out would be a quick/easy way to see if they are causing the problem.

---

### Post by peddy on 2008-10-03
Ok, I added my DNS servers. Now I get this in the error log:

```
Oct  4 13:26:38 moonshine dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Oct  4 13:26:38 moonshine dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Oct  4 13:26:38 moonshine dhcpd: All rights reserved.
Oct  4 13:26:38 moonshine dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Oct  4 13:26:38 moonshine dhcpd: Wrote 0 leases to leases file.
Oct  4 13:26:38 moonshine dhcpd: 
Oct  4 13:26:38 moonshine dhcpd: No subnet declaration for bnep0 (0.0.0.0).
Oct  4 13:26:38 moonshine dhcpd: ** Ignoring requests on bnep0.  If this is not what
Oct  4 13:26:38 moonshine dhcpd:    you want, please write a subnet declaration
Oct  4 13:26:38 moonshine dhcpd:    in your dhcpd.conf file for the network segment
Oct  4 13:26:38 moonshine dhcpd:    to which interface bnep0 is attached. **

```

bnep0 is my bluetooth adapter. How do I write a subnet declaration for it?

Thanks

---

### Post by Iowan on 2008-10-03
Kinda looks like the same error message with a different face.  Will you be serving DHCP Addresses through there? (Does BT use IP's?) Does bnep0 have an IP address (what is it?) I remember another thread wanting to limit DHCP services to one of two NIC's - I'm wondering if there's a way to bind to a specific interface.

Still getting the "Failed to start" message?

In studying **man dhcpd.conf**, it appears that if bnep0 has an IP address, you'll need to set up a subnet declaration - even if you don't serve DHCP addresses there.

---

### Post by peddy on 2008-10-03
I will be serving DHCP addresses to the BT device, yes. 

here's the last line of the error:

```
Oct  4 13:26:38 moonshine dhcpd: Not configured to listen on any interfaces!

```

Also, the device is not found for some reason?
```
apc@moonshine:~$ ifconfig bnep0
bnep0: error fetching interface information: Device not found

```

I'm actually trying to get [this](http://www.howtoforge.com/bluetooth_pand_debian_etch) working; a bluetooth PAN with internet sharing. I'm having trouble understanding these steps: 


> Change the IPs and network settings as you like, just make sure to also reflect it in your dhcp.

does this mean I have to get dhcp working *before* I can follow this guide?

Thanks a lot for your help, I appreciate it.

---

### Post by Iowan on 2008-10-03
Interesting article (gotta love howtoforge.com).  So, how did you set up bnep0 in your **/etc/network/interfaces**? The static address you used would be the router address - it's subnet (x.x.x.0) would need to be set up in **/etc/dhcpd3/dhcpd.conf**.
I'm not sure I can explain why interface is not being seen (unless the *interfaces* file is misconfigured).

As usual - I thought of something later... Are you actually serving addresses on eth0 - or did we work on it only because that's where the error pointed?  If you don't really want to serve DHCP addresses via eth0, it could be defined as a subnet (without a range, routers, etc) to squelch the error messages.

---

### Post by peddy on 2008-10-03
Ok, here's my section for bnep0 in /etc/network/interfaces

```
iface bnep0 inet static
          address 10.0.254.1
          netmask 255.255.255.240
		  
post-up iptables -t nat -A POSTROUTING -s 10.0.254.0/24 -j MASQUERADE
post-up iptables -A FORWARD -i bnep0 -o eth0 -j ACCEPT
post-up iptables -A FORWARD -o bnep0 -i eth0 -j ACCEPT
pre-down /etc/init.d/dhcp3-server stop
```

> Declare a subnet for the PAN segment, should be the subnet you used for the bnetp device in /etc/network/interfaces. **Replace the option** *routers 10.0.254.1*; **with the IP you have given your bnep0 interface in /etc/network/interfaces.**

I'm not serving addresses on eth0, only bnep0. Also, this part ```
post-up iptables -A FORWARD -o bnep0 -i eth0 -
``` in /etc/network/interfaces, should I replace eth0 with wlan0 since I'm using a wireless network? I'm a beginner in this area.

I get this error with bnep0 now: the good news is that at least it's recognizing the interface.
```
~$sudo ifup bnep0
bnep0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
bnep0: ERROR while getting interface flags: No such device
Failed to bring up bnep0. 
```

Thanks

---

### Post by Iowan on 2008-10-03
> **peddy said:**
> I'm not serving addresses on eth0, only bnep0. 
If you're not serving addresses on eth0, the quick/dirty approach would be to comment out (#) the *options* lines and the *range* line. If the error/warning about eth0 subnet comes back... 

You'll need to build a subnet section for bnep0 similar to the How-To.
> in /etc/network/interfaces, should I replace eth0 with wlan0 since I'm using a wireless network? I'm a beginner in this area.Sounds like a plan... I've no experience in Bluetooth - almost none in wireless.
> I get this error with bnep0 now: the good news is that at least it's recognizing the interface.Well, maybe...

---

### Post by peddy on 2008-10-03
> **Iowan said:**
> 
You'll need to build a subnet section for bnep0 similar to the How-To.


Could you please explain how to do this? Thanks :P

Some info, maybe it'll help:
wireless router: 192.168.1.1
my IP: 192.168.1.2

---

### Post by peddy on 2008-10-03
[IMG]http://img.photobucket.com/albums/v655/rrclimber/smilies/bananaWrench.gif[/IMG][IMG]http://img.photobucket.com/albums/v655/rrclimber/smilies/bananaWrench.gif[/IMG][IMG]http://img.photobucket.com/albums/v655/rrclimber/smilies/bananaWrench.gif[/IMG][IMG]http://img.photobucket.com/albums/v655/rrclimber/smilies/bananaWrench.gif[/IMG]

I DID IT!!

It didn't even work in Windows with official drivers and stuff... But it works in Ubuntu! I can now access the internet from my mobile phone!


EDIT: -.- ok, my phone managed to load 1/2 of Google (the page but not the pics). bnep0 was showing in ifconfig, but now it's gone :confused:

ifup bnep0 says the iface is already configured.

I'm getting closer!

Regards
Peddy

EDIT: I managed to grab the output of ifconfig bnep0; 

```
bnep0     Link encap:Ethernet  HWaddr 00:11:67:c7:f1:dd  
          inet addr:10.0.254.1  Bcast:10.0.254.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1684 (1.6 KB)  TX bytes:1072 (1.0 KB)

```

Internet stops working after a few minutes.

---

