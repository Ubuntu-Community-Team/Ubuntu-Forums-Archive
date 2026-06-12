---
title: "network manager and PEAP 802.1x under WEP"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by lirelent on 2006-10-26
My universities like many universities use PEAP over 802.1x to secure their wireless networks, but it does NOT use WPA.  It distributes WEP keys via 802.1x, and therefor really uses WEP.  So I know network manager is working fine because I can connect to my home WPA personal network (something that is very cool to be able to do so easily :D ) So when I try to connect to my university's network with network manager it detects correctly that it's a WEP network and asks me for a WEP key, but there doesn't seem to be an option to get the WEP key via 802.1x.  Is there a way to do this in network manager, I'd like to avoid using xsupplicant directly (and WPAsupplicant doesn't seem to support 802.1x in this WEP based application? :-k ) because it seems that it would conflict with network manager and I like network manager so much.

Any help would be greatly appreciated

P.S. I'm running edgy on D620 2.16GHx Core Duo with integrated Intel Corporation PRO/Wireless 3945ABG

---

