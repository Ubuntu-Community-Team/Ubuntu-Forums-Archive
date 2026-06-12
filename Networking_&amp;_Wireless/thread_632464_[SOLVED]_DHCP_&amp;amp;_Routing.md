---
title: "[SOLVED] DHCP &amp;amp; Routing"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by jmflyer on 2007-12-05
No issue here, just curious as to why...

I'm using Linux as a router (or forwarder) for a small network.  I have 3 subnets that are routed through this box.   DHCP resides on my Windows domain controller on subnet 1.  I would expect that clients on subnet 2 & 3 would not get IP address assigned via DHCP as I have no DHCP relay installed.  However, they do.

Note:  The clients connect to a managed switch, each subnet is a different VLAN - so DHCP HAS to be passed through a router/relay.  To prove this - if I do this same test but use Redhat EL4 - DHCP doesn't make it through.

The linux router is a regular Dapper server install, with nothing else installed.  To enable routing I simply:  "echo 1 > /proc/..../ip_forward".

I'm happy that Dapper is doing this - just a little confused on how.  I've looked online, and through the kernel menuconfig to see if I could figure out how, but I'm stuck.

Thanks!

---

### Post by mellowd on 2007-12-05
DHCP uses UDP over ports 67 and 68. Therefore the packets will go through any IP router that is in their way

---

### Post by jmflyer on 2007-12-05
UDP Broadcasts (like DHCP) are not routed through any IP router.  

For instance, on a Cisco you have to configure an 'ip helper-address'.  On Foundry gear, it's a bootp-gatway &/or ip helper-address.  Or, you have to install DHCP relays on those subnets.

---

### Post by jmflyer on 2007-12-05
:redface:  Found my answer....

The DHCP Server (which I don't have physical access to) has multiple NICs and therefore was connected to all VLAN's.  The fact that it didn't work with my red-hat EL4 experiment was a fluke.

The relief outweighs the embarrassment.  The world has order again :-)

---

