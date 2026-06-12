---
title: "IP running W2000 and Ubuntu"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Dawgwalker on 2008-06-16
If W2K and Ubuntu 8.04 run on the same machine and that machine networks on the same router port will the IP address be the same in W2K and Ubuntu? 

If the DHCP server leases an IP address to the W2K nic what happens when Ubuntu boots?

First exposure to Ubuntu so striving for understanding and appreciate universal help.

---

### Post by chili555 on 2008-06-16
> will the IP address be the same in W2K and Ubuntu?Probably, but not assuredly.> If the DHCP server leases an IP address to the W2K nic what happens when Ubuntu boots?When you shut down W2K, the interface goes down and the lease is released back to the DHCP server. When you boot Ubuntu, the released number is available, if needed.

---

