---
title: "ddns dhcp update of bind : client timeout / server takes to long"
date: 2018-06-10
forum: Networking &amp; Wireless
---

### Post by hanasaki on 2018-06-10
have dhcp and bind setup so dhcp pushes hostname records to bind based on the hostname requested by the client.

updates work ok and seem to take place in the same second (based on log files) however the client sometimes times out (seen by DHCPDISCOVER 2 or more times on the client [example from ifdown eth0; ifup eth0) also seen by browser and video stream play back for a regular renewal hanging/pausing.

Thoughts for resolving this by client / server configs?

---

