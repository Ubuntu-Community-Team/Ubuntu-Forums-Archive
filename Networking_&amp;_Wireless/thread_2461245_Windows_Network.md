---
title: "Windows Network?"
date: 2021-04-27
forum: Networking &amp; Wireless
---

### Post by hairyjew117 on 2021-04-27
I've never seen this display before. When I click on Files and go to Other Locations I get an option for Windows Network in the Networks Category. Is this normal or am I actually connected to an unauthorized network without my permission? Clicking on it just gives me an eror ```
Failed to retrieve share list from server: No such file or directory
```

[IMG]https://i.imgur.com/46MaVVk.png[/IMG]

---

### Post by scorp123 on 2021-04-27
Looks perfectly normal. If there are no machines inside your network that offer SMB shares then there's nothing to show.

---

### Post by scorp123 on 2021-04-27
If you really really want to be sure who else / what else is on your network, you could do a quick scan with **"nmap"** (not installed by default) and check your local network for unknown machines.

My network is 192.168.1.0 with the netmask 255.255.255.0, also known as "192.168.1.0/24". So to do a quick scan I'd do:
```
nmap 192.168.1.0/24
```

This would then list everything that's online here, including WiFi access points, printers, scanners, NAS, ChromeCast dongles, SmartTV's, Android TV boxes, my Android smartphone ... everything.

A bit of a warning too: NEVER EVER scan someone else's network (e.g. Internet hostnames, Internet web sites, Internet IP addresses ...). A network scan can easily be detected by firewalls and the target will know you scanned them. This could trigger hostile actions against you, e.g. them calling your ISP and having you disconnected from the Internet. So ... Don't ever scan someone else's network or IP address!

---

