---
title: "Ubuntu Desktop DHCP Client - How to avoid setting DNS Servers?"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by microsatan on 2007-05-07
Hello

I have an interface with is set to get an IP via DHCP through my ISP, but I dont want to get DNS information from my ISP. In other words I dont want my resolve.conf file overwritten by the dhcp client. How can I stop this happening? Reason is that I am running bind so dont need DNS information from the ISP.

---

### Post by spd106 on 2007-05-08
This is usually achieved through an option in the /etc/dhcp3/dhclient.conf file. Specifically you remove domain-name-servers from the request line.

---

