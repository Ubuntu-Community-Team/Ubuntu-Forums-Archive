---
title: "How to open ports?"
date: 2005-07-31
forum: Networking &amp; Wireless
---

### Post by Aero-Z on 2005-07-31
I found similar commands from Fedora site, but saving the configuration is different. Same is:

# /sbin/iptables -I INPUT -p udp --destination-port 6881:6881 -j ACCEPT

But saving is different:

# /sbin/iptables-save > /etc/sysconfig/iptables

Ubuntu doesn't have /sysconfig/iptables so where or how do I have to save the new configuration?

---

### Post by amohanty on 2005-07-31
[https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29](https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29)

HTH

AM

---

### Post by Aero-Z on 2005-07-31
[QUOTE=amohanty][https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29](https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29)

HTH

AM[/QUOTE]
HAHAA, thank you very much :)

---

