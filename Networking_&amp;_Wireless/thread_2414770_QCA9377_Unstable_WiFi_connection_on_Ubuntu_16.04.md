---
title: "QCA9377 Unstable WiFi connection on Ubuntu 16.04"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by igosyee on 2019-03-14
[COLOR=#242729][FONT=Arial]Hey!

I have a problem with Wi-Fi on a Dell laptop with a Qualcomm Atheros QCA9377 802.11ac wireless network adapter. 
WiFi somewhere every 5-10 minutes just stops receiving and sending data. I can not connect to the router (192.168.1.1) too. If I just reconnect to the hotspot, then the next 5 minutes Wi-Fi is working.
With ethernet everything works without issues. On the second OS win10, wifi also working without issues.

I tried this: [https://ubuntuforums.org/showthread.php?t=2355396](https://ubuntuforums.org/showthread.php?t=2355396) , but nothing has changed.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][I]
Result of wireless info script : [https://paste.ubuntu.com/p/dxcBcJxz7W/](https://paste.ubuntu.com/p/dxcBcJxz7W/)

[/I][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does anyone have any ideas on how to fix this annoying problem?[/FONT][/COLOR]

---

### Post by jeremy31 on 2019-03-14
Go into the router settings, and set it to channel 9 rather than auto, and set the bandwidth to a setting other than auto

---

### Post by igosyee on 2019-03-28
> **jeremy31 said:**
> Go into the router settings, and set it to channel 9 rather than auto, and set the bandwidth to a setting other than auto

Thank you! I've changed bandwidth from auto to 20MHz and everything is fine.

---

