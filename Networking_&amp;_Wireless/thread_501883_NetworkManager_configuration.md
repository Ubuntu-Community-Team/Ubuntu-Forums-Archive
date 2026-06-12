---
title: "NetworkManager configuration?"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by MyR on 2007-07-15
Is there any way to configure the networkmanager to not add my router's nameserver to the list in /etc/resolv.conf ? I edit it myself but it generates a new one whenever i connect.
Thanks!

---

### Post by altaaa on 2007-07-17
Can you edit the DCHP server properties in your router? If so, just remove the router's IP address there in the DNS server list...

---

### Post by MyR on 2007-07-18
I figured it out.
i just had to open /etc/dhcp3/dhclient.conf
and add this line
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

---

