---
title: "Bringing up Vlan interface on startup"
date: 2021-01-16
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2021-01-16
I am running Ubuntu server 20.  I am trying to bring up my vlan interface.  Here is the script:
```
[FONT=monospace][COLOR=#000000]#!/bin/bash[/COLOR]
[ "$IFACE" = "enp4s0" ] || exit 0
vconfig add enp4s0 2
[/FONT]
```
Here are the permissions for the file: [FONT=monospace][COLOR=#000000]-rwxr--r-- 1 root root   67 Jan 16 07:18 [/COLOR][COLOR=#54FF54]**vlan2**[/COLOR]
[COLOR=#000000][/COLOR]Upon startup, the interface does not come up. [/FONT]

---

### Post by TheFu on 2021-01-16
I take it using a netplan didn't work? For a non-trivial example:
[https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629](https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629)
[https://netplan.io/examples](https://netplan.io/examples)

I don't use vlans so those links are the extent of my help, such as it is. ;(

---

