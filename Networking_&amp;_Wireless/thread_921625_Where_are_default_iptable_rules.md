---
title: "Where are default iptable rules?"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by egeex on 2008-09-16
Hello,

1st attempt with unbutu.
i have installed server 8.04 and have it up and running. i am trying to configure new default iptable rules and having difficulty. I have created my rules saved them to a file and modified the /etc/network/interfaces as suggested here [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo). when i reboot or restart networking I get no address on my eth0 interface and no routes at all. all networking down. when i remove my changes and reboot/restart networking eth0 is back to normal, routes are present and iptables has a new set of rules. where are these rules coming from and how can i modify them.

any suggestions are appreciated

regards
mjs

---

### Post by nixscripter on 2008-09-17
What exact changes have you made? Post **/etc/iptables.rules** and **/etc/network/interfaces** (before and after your modifications).

---

