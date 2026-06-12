---
title: "ARP Requests Being Sent For Different Subnet"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by bsntech on 2015-11-25
Have an Ubuntu 14.04 DNS server running bind.  Let's say it is on subnet 216.107.250.x and subnet mask is 255.255.255.128.  Gateway is set to 216.107.250.1.

Getting complaints that there are client computers that are not able to obtain DNS lookups.  These clients are in the 216.107.249.x range with a subnet of 255.255.255.0.

Using WireShark, the DNS requests are coming in from the clients and are getting resolved properly.

But then there are a lot of ARP requests "Who Has IP 216.107.249.x?"  Obviously this is not going to be replied to - because it is on a different network.

Why in the heck is this happening?  No ARP requests should be sent for something not on the same network.  And because of this, the clients are not getting responses from the server.

The /etc/network/interfaces file is statically set.  Only one NIC in the system:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 216.107.250.2
        network 216.107.250.0
        netmask 255.255.255.128
        broadcast 216.107.250.127
        gateway 216.107.250.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 127.0.0.1 8.8.8.8

Would consider myself a pro at networking (do it as a regular task) but this one just makes zero sense.

Thank you for any help.

---

### Post by CharlesA on 2015-11-25
I would guess the subnet 216.107.249.x isn't configured correctly and is forwarding packets or traffic to the .250 subnet.

Are these physical subnets or are they set up as VLANs?

---

### Post by bsntech on 2015-11-25
There are a total of four subnets; Seems anything to the other two subnets are fine, but to the .249 subnet it doesn't work.

All of the subnets are connected to the same switch/router.  It is a MikroTik device that has several ports on it - which then branches out to other locations/switches.  So everything is to come back to the MikroTik router/switch - which has several IP addresses on it as the default gateway for each subnet.  Then the MikroTik device is responsible for routing between those subnets.

But what would even be prompting Ubuntu to be doing ARP requests for something clearly not on the same network as well?  Seems to be against all networking knowledge that ARP requests are being sent out for something on a different subnet.  I'm sure my general /etc/network/interfaces file is proper.

---

### Post by slickymaster on 2015-11-25
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by bsntech on 2015-11-25
Additional info if it is helpful.

I can now ping on that 249.x subnet.  Absolutely nothing else was changed.

But when doing a ping to an IP, say 216.107.249.87, the router is seemingly returning the response:

PING 216.107.249.87 (216.107.249.87) 56(84) bytes of data.
From 216.107.250.1: icmp_seq=1 Redirect Host(New nexthop: 216.107.250.1)
64 bytes from 216.107.250.1: icmp_seq=1 ttl=63 time=18.4 ms

So, I guess why is the router issuing a Redirect Host with it's IP address, then responding to the pings using it's IP address instead of the pings coming from the actual address?

All very confusing situation here.

---

### Post by bsntech on 2015-11-25
Welp, the TCP stack in Windows is obviously different than Linux/Ubuntu.

Still not able to get to the bottom of this problem.

SOME IP addresses in the 249 subnet are pingable on the Ubuntu server, some not.

I loaded a Windows XP computer up real quick and put it on the same subnet that the Ubuntu server is part of.  Started pinging - and it does ping all of the IP addresses in the 249 subnet successfully - even when the Ubuntu one fails.

This makes no sense.  I'm sure there isn't a 'bug' in the TCP stack of Linux/Ubuntu, but it makes absolutely no sense that Ubuntu has entries in the arp cache for machines in another subnet.  The Windows XP computer doesn't.  Sure, the subnets are all connected to the same switch.  Is there any kind of configuration that would potentially ignore all arp packets from other subnets - or prevent the Ubuntu server from sending out arp requests for addresses in other subnets?

Can't say this is the root of the problem, but obviously Wireshark is showing the Ubuntu server sending out arp requests to the IP address in the other subnet that I'm trying to ping.

---

### Post by bsntech on 2015-11-26
This has been solved.

Linux obviously doesn't exactly play by the regular rules of the TCP stack like Windows machines do.

A ping to x.x.249.75 worked all the time; no problems.  Why?  It was a Linux-based machine.  Based on other searching, I see that Linux machines will respond to ARP requests - even if it is in a different subnet.  So the Linux server sent ARP requests to 249.75 and they were getting responses.  Hence why this IP address continued to reply to ping requests.

I restarted the Linux server.  Did a ping to an IP address that was problematic (x.x.249.76).

An ICMP Redirect was received from the router (x.x.250.1) saying "Hey, you can talk to x.x.249.76 directly and you don't need to go through me).  Immediately once that was received, the ping responses timed out and quit.  That queued the ARP requests to the 249.6 client and, of course, they were not responded to.

The router is a MikroTik router and I see it is based on Linux as well.

Since these four subnets were all on the same router, the MikroTik device **THOUGHT** that it did not need to relay the packets or be the 'middle man'.  Wrong.

The solution was to update the /etc/sysctl.d/10-network-security.conf file and these lines were added:

    net.ipv4.conf.all.send_redirects = 0
    net.ipv4.conf.default.send_redirects = 0
    net.ipv4.conf.all.accept_redirects = 0
    net.ipv6.conf.all.accept_redirects = 0
    net.ipv4.conf.default.accept_redirects = 0
    net.ipv6.conf.default.accept_redirects = 0

This told the Linux server to completely ignore any ICMP redirects.

Server was restarted.  Starting pinging x.x.249.76 and the redirect notices still were received, but were ignored and the server continued to successfully ping the IP address.

If only standards were adhered to sometimes.. geesh.

---

