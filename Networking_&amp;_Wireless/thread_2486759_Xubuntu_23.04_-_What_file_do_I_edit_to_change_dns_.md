---
title: "Xubuntu 23.04 - What file do I edit to change dns servers?"
date: 2023-05-09
forum: Networking &amp; Wireless
---

### Post by Evil Wayz on 2023-05-09
apparently resolvconf is now resolveconf.service which doesn't  and I don't know what cfg file to edit to change dns servers.

---

### Post by #&amp;thj^% on 2023-05-09
Why not through  NetWork Manager?
EDIT: How ever if you need a down and dirty approach:
```
sudo nano /etc/resolv.conf

```
Now add your DNS you want to:
Example:
```
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 8.8.8.8
options edns0 trust-ad
search mynetworksettings.com

```
now that's just sym-link so we need to lock it down with a flag:
```
sudo chattr  -f   +i   /etc/resolv.conf

```
Now don't forget about that locked file for future Dist-Upgrade.
Check with:
```
( nmcli -f IP4.DNS,IP6.DNS dev list || nmcli -f IP4.DNS,IP6.DNS dev show ) 2>/dev/null | awk '/DNS/{print$NF}'
```
Mine: ```
8.8.8.8
192.168.1.1

```

---

