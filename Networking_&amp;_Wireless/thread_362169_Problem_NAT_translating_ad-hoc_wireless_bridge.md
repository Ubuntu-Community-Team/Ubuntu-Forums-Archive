---
title: "Problem NAT translating ad-hoc wireless bridge"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by paulhollow on 2007-02-15
Here's an interesting one...  I have a simple NAT translation server set up with a variety of machines behind it, all working well.  They can all see each other on the local subnet and can all access the WWW on the other side of the NAT translation machine.  The local subnet is 192.168.0.x, 192.168.0.1 being my gateway, which also runs a DNS server.

So, local settings are:
 - IP: 192.168.0.x
 - Mask: 255.255.255.0
 - Gateway: 192.168.0.1
 - DNS: 192.168.0.1

This all works well.  BUT i have now added an ad-hoc wireless bridge to another machine too far away to cable to.  This machine can see, ping and even mount samba servers within the internal subnet, but is unable to access the outside world.  it is set up like...

lan----(bridge, 192.168.0.5).... wireless ....(bridge, 192.168.0.6)----(comp 192.168.0.7)

.0.7 can see the gateway (.0.1), can ping it, and can receive resolved DNS requests from the DNS server running on .0.1.  However, as soon as it tries to send anything to the outside world, the return packets are dropped.

I think this is due to the NAT translation which is receiving packets from bridge .0.5, but when packets go back to it, .0.5 does not know where to send them and they are dropped.

How do i ensure that both MAC addresses (from each wireless bridge end) are preserved for the return journey?

Anyone any ideas?  Any help much appreciated!

Paul

---

### Post by spd106 on 2007-02-15
I'm no expert on bridges, but maybe you should check the bridge's forwarding table for errors. **brctl show br0** or something like that.

---

