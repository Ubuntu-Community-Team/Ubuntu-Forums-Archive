---
title: "Network data drops out and returns intermittently"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by brent26 on 2015-06-11
[COLOR=#464445][FONT=Verdana]About 2 weeks ago I started having some network issues. [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]I can connected to wifi fine; but it seems like data stops and starts relatively randomly. So 5 min on; everything great; then accessing a website - browser just shows connecting for ages -- sometimes it times out; sometimes it connects [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]Then the data will come back - and everything is fine for a couple more minutes. [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]I'm on Ubuntu 14; and [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]'grep NetworkManager /var/log/syslog*' [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]Doesn't show up any interesting logs [/FONT][/COLOR]

[COLOR=#464445][FONT=Verdana]Just wondering if you guys had any thoughts how I could investigate further. 

Thanks
[/FONT][/COLOR]

---

### Post by Pilot6 on 2015-06-11
Please give output of

lspci -knn | grep Net -A2

---

