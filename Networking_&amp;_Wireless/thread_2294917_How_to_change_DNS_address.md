---
title: "How to change DNS address"
date: 2015-09-14
forum: Networking &amp; Wireless
---

### Post by arjun13 on 2015-09-14
Hello, I am new to Ubuntu and I wanted to change the DNS address. If I try to edit it in "/etc/resolv.conf", the changes are temporary. For the file "/etc/init.d/resolvconf", to make the changes, I need to add the line " dns-nameservers X.X.X.X". But my Wi-Fi settings are dynamic and not static. And what I read was the lines for editing should start with "iface wlan0 inet static".

What should I do? Currently, I am using Ubuntu 15.04 [3.19.0-15-generic #15-Ubuntu; x86_64]

Thanks!

---

### Post by SeijiSensei on 2015-09-14
The best solution is to edit the DNS server settings on the router.

On Kubuntu, which I use, the graphical NetworkManager can be configured to get only the IP address from the DHCP server and use locally-defined DNS server addresses.  I'd be surprised if the same options are not available via the graphical manager in regular Ubuntu.

---

