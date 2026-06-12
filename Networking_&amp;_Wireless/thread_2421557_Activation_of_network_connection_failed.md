---
title: "Activation of network connection failed"
date: 2019-06-23
forum: Networking &amp; Wireless
---

### Post by gduff567 on 2019-06-23
Installed ubuntu 18.04.2 LTS yesterday on Lenovo Z580 and everything was working perfectly. Come back today and wifi can no longer connect, just says "Activation of network connection failed". 

Internet works over ethernet so I'm not sure what it is. Thanks.

FIXED: After looking at wireless report I saw that the bcma and bcmsmac were blacklisted in multiple locations. Removed the blacklist and working again.

---

