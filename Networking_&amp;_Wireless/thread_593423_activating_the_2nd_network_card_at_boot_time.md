---
title: "activating the 2nd network card at boot time"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by boondocks on 2007-10-27
Just installed Ubuntu 7.10 Server.
The physical system has 2 network cards.
Both work.  Tested them with the Live CD.

The 7.10 server only activates the eth0 card.
How to I get the 7.10 server to activate the 2nd network card too?

I want both eth0 and eth1 to be DHCP clients at boot time.

---

### Post by Lambert on 2007-10-27
> **boondocks said:**
> Just installed Ubuntu 7.10 Server.
The physical system has 2 network cards.
Both work.  Tested them with the Live CD.

The 7.10 server only activates the eth0 card.
How to I get the 7.10 server to activate the 2nd network card too?

I want both eth0 and eth1 to be DHCP clients at boot time.

Open the file /etc/network/interfaces. You should see a line for both nics that say this

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

the auto stanzas should bring up both interfaces based on your network information. In this example both nics come up and configure using a dhcp server. For more information see mana page of interfaces

---

### Post by boondocks on 2007-10-27
Thanks.  That worked.

---

