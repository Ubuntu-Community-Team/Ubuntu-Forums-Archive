---
title: "Manually set DNS server after connecting to VPN"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by vwenberg on 2013-12-25
I have a shell script from my VPN provider that connects me to their servers. I can connect fine but my DNS servers are not set after connecting. How would I go about adding this manually to the script so I can reset my DNS servers after connecting?

Much thanks!

---

### Post by devine.steve on 2013-12-25
How about:
echo "nameserver 8.8.8.8" >>/etc/resolv.conf

---

