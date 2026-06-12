---
title: "DNS settings in Network Manager"
date: 2017-12-07
forum: Networking &amp; Wireless
---

### Post by phil215 on 2017-12-07
Checking a few things after changing ISP recently, I issued the Network Manager command:
 ```

 nm-tool | grep DNS
 
```
 To my surprise two redundant DNS names were still present. Currently the IPv4 setting is “Automatic (DHCP)” and I've added the new DNS names in the “Additional DNS servers” field.
 The Primary DNS points to the router, which is understandable since that device has the new ISP's DNS names stored.
 
 The grep output is not really a problem, because my connection and routing are working well, it's just a little untidy. Also, it's slightly disconcerting to see the old DNS names when they are not explicitly stated in the Edit Connections box. This leads me to wonder where the stale information is coming from. It appears that Network Manager has previous DNS names stored in a system file. How are the DNS names set and how can I remove the old names?
 I've been looking into this with various searches, but can't find the definitive answer, so any help would be greatly appreciated.

---

