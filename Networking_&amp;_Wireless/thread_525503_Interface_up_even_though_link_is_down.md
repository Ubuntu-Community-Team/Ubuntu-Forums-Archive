---
title: "Interface up even though link is down"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by ThomasNovin on 2007-08-14
Hey all

I don't know if this is defective by design or if it's a bug but if I unplug my network interface, the interface is still up, the routing entries are still there and the interface address is also still there.

I think that the second you pull the link, the interface should disappear. The same goes for when I plug the link back in, if the interface is using DHCP the dhcpclient should immediately broadcast DHCP-requests.

To go a little further, it would be nice to get a confirmation that your network link is actually working too. I guess this could be done by arping for the default gateway and if we get a reply on the arp, it's safe to asume that the connection is in a working state.

Comments? Is this issue already discussed somewhere?

Rgds...

---

### Post by bdk6m2007 on 2007-08-20
I've observed the same behavior and it doesn't make a lot of sense to me, either.  Would love a definitive answer from someone in the know......

---

### Post by ThomasNovin on 2007-08-20
This looks interesting, maybe this is fixed in NM which is provided by Gutsy:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/115495](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/115495)

---

### Post by raijinsetsu on 2007-08-20
That's normal behavior for a network device. You need another Daemon that detects link status, and deals with it. KDE comes with KNetworkManager. I believe Gnome has a similar program.

---

### Post by ThomasNovin on 2007-08-20
> **raijinsetsu said:**
> That's normal behavior for a network device. You need another Daemon that detects link status, and deals with it. KDE comes with KNetworkManager. I believe Gnome has a similar program.

Yes, this would be Network Manager. I actually was talking about NM in my first post. Since this is something that is enabled per default in Ubuntu Feisty I didn't even think about the fact that the other *buntus are using other methods.

---

