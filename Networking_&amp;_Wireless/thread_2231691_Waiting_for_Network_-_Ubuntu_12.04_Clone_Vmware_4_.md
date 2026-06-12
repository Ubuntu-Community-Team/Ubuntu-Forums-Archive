---
title: "Waiting for Network - Ubuntu 12.04 Clone Vmware 4 Nics"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by cake5 on 2014-06-27
Hello,

i have the following issue. When I clone a template with more than one nic i'll get the message "Waiting up to 60 more second for network configuration". I have 4 nic attaced in the template and deleted /etc/udev/rules.de/70*. With only one nic attaced evertying is fine.  Is there a solution for this probem or workarround?

---

### Post by praseodym on 2014-06-27
Change "false" to "true" in the file /etc/NetworkManager/NetworkManager.conf and reboot, otherwise the network manager can not handle the manual config in the /etc/network/interfaces

---

