---
title: "Feisty - Ethernet interface wierdness"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by gwoollett on 2007-05-06
I recently upgraded to Feisty from Edgy and am having no end of problems with network-admin and ip assignments to ethernet cards.

On two of the three cards in one my machine routinely loose their statcially set ip addresses.
ie card is listed  by ifconfig but no ip address.  The network admin program is very hit and miss.
Using the ifup & down commands or networking restart seems to get this right again until the next time.

The robustness of the ip configuration in Feisty seems to be very flakey when compared to earlier releases.
I've now had this problem on two different machines.

Anyone else having problems like this?

---

### Post by netztier on 2007-05-06
> **gwoollett said:**
> I recently upgraded to Feisty from Edgy and am having no end of problems with network-admin and ip assignments to ethernet cards.

On two of the three cards in one my machine routinely loose their statcially set ip addresses.
ie card is listed  by ifconfig but no ip address.  The network admin program is very hit and miss.
Using the ifup & down commands or networking restart seems to get this right again until the next time.

The robustness of the ip configuration in Feisty seems to be very flakey when compared to earlier releases.
I've now had this problem on two different machines.

Anyone else having problems like this?

Sounds like ethX assignments get mixed up from time to time.

Check the** /etc/iftab** file for wrong/stale MACaddress to ethX assignments, and best use it to nail down which interface (referenced by MAC address) gets which ethX name:

```

marc@blaze:/etc$ more iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0E:0C:D0:B4:D3 arp 1
eth2 mac 00:A0:C9:98:82:0E arp 1
eth3 mac 00:50:8B:07:E9:83 arp 1
```

best regards

Marc

---

