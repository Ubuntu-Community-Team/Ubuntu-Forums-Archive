---
title: "Creating vlan on boot-up"
date: 2020-12-09
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2020-12-09
I am running [FONT=monospace][COLOR=#000000]20.04.1 LTS (Focal Fossa) Ubuntu server.  In my yaml config file for a new vlan interface, I have the following:
```
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]eth0.4:[/COLOR]
      dhcp4: no
      addresses:
        - 192.168.130.2/24
      gateway4: 192.168.130.2
      nameservers:
        addresses: [1.1.1.1]
  version: 2
[/FONT][FONT=monospace][COLOR=#000000]
```
[/COLOR]I've already done a [/FONT][COLOR=#333333]modprobe 8021q.  When I do a netplan apply, the new interface is not created.  I also have eth0 defined, which works just fine. [/COLOR]

---

