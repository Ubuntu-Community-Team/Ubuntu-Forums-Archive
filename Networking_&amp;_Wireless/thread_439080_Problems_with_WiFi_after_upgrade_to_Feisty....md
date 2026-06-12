---
title: "Problems with WiFi after upgrade to Feisty..."
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by knichel on 2007-05-10
I have 2 problems...
1)  After the upgrade to Feisty, I can no longer have my wifi router set to *NOT* broadcast my ssid.  THe only way I get a connection is to broadcast it.  As soon as I turn broadcasting off, my connection dies...

2)  I have a route in my routing table that I need to remove *every* time I reboot.  It is 169.254.0.0 255.255.0.0  ra0.  I wish to remove it permanently.  How do I remove it for good?


--
Thanks  in advance,
Mike

---

### Post by javahollic on 2007-05-15
I want the asnwer to this also, as It may be related to a 'Destination host unreachable' problem I logged in another thread...:(

---

### Post by javahollic on 2007-05-15
I had a can't ping Internet hosts (routing issues, I linked to this problem).

I foudn a post that gave me the followin *temporary* fix, that can be applied in /etc/rc.local until somebody figures out the correct way to do it, namely:

#!/bin/bash
# zaps the 169 route, resets to use my wireless router on eth1
#
ip r d default dev eth1
ip r d 169.254.0.0./16
ip r a default via 192.168.1.1 dev eth1

ad, lo, I have Synaptic updates.:guitar:

---

### Post by johntelthorst on 2007-05-20
Not being able to connect to wireless networks with the SSID not broadcasted seems to be a known issue.  As far as I know you have to use wap_supplicant if you want to connect.  Hopefully it will be patched.

---

