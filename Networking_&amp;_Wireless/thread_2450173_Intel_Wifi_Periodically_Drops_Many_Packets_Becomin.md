---
title: "Intel Wifi Periodically Drops Many Packets Becoming Unusable"
date: 2020-09-08
forum: Networking &amp; Wireless
---

### Post by vagary on 2020-09-08
I'm using Ubuntu 20.04 on a ThinkPad with an Intel wifi card. My wifi connection will go through periods of dropping many packets to the point where it becomes unusable. The connection never actually drops and the icon shows good signal strength. Turning off wifi and turning it back on again always fixes the problem, but sometimes only for a minute or two until it happens again. Wired connections work reliably.

Things I've tried:
[LIST]
[*]Switching routers
[*]Adjusting power saving mode
[*]Switching to wicd
[*]Setting my iw region
[*]Turning off IPv6
[*]Reconfiguring all the network packages
[/LIST]

...And any other proposed fix I can find. It seems as though the problem has been getting worse over the course of the last year. I have attached the output from the wireless-info script and sample logging from `ping -i 10 -W 10 192.168.0.1` when I'm sitting 2 feet from the router. Thank you!

[ATTACH]286923[/ATTACH]

[ATTACH]286922[/ATTACH]

---

### Post by CelticWarrior on 2020-09-09
WICD isn't a solution, never.
Changing the wireless settings to WPA2-AES is. You say you switched routers but never checked the wireless settings?
Always WPA2-AES, not any WPA/WPA2 mixed mode and never TKIP which has been deprecated many years ago.

---

### Post by vagary on 2020-09-21
Thanks, I tried setting my router to WPA2-PSK with AES. It did not solve the problem. Any other suggestions?

---

