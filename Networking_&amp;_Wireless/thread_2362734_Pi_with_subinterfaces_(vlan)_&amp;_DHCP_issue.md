---
title: "Pi with subinterfaces (vlan) &amp; DHCP issue"
date: 2017-06-01
forum: Networking &amp; Wireless
---

### Post by armegeden on 2017-06-01
Sorry if this isn't the correct forum for a Rasberry Pi issue, but I assume it's a basic Ubuntu networking issue...

I have a Rasberry Pi serving DHCP to two VLANs.  Both eth0 (untagged/native on switch) and eth0.77 (tagged 77 on switch) are working properly but I am receiving unexpected DHCP packets on the subinterface.

Every ~30 seconds, [eth0.77 appears to be sending a DHCP Discovery]("http://imgur.com/a/fFsJC"), then eth0.77 sends back the DHCP Offer (as a DHCP server should); Request/Acknowledgement are never created (expected? since all eth are Static -- but why is the Request being generated at all?).

It's odd.  I assume the Pi/eth0.77 is doing some type of proactive DHCP server discovery via the DHCP broadcast, but I do not see this behavior on the regular eth0 interface.

Any ideas?

(Switchport is a trunk with native at 1 and allowing tagged vlan77)

Thanks for any help

---

