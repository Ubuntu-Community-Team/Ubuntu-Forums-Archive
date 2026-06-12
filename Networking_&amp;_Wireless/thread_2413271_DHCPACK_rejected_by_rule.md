---
title: "DHCPACK rejected by rule"
date: 2019-02-23
forum: Networking &amp; Wireless
---

### Post by l.j.b. on 2019-02-23
Hey guys,

I've encountered an issue with my ethernet connection and was wondering if anyone knows the problem and can give me a hint.
Since a few days, my PC running Ubuntu desktop 18.04 LTS can not connect to the Internet via Ethernet anymore. I am not aware of having changed anything, but I installed some software updates.
I tried to ping google.com, 8.8.8.8 and 8.8.4.4, but always get "network is unreachable". I also rebooted, and restartet the network manager via [COLOR=#E5E1D8][FONT=&quot]systemctl restart network-manger[/FONT][/COLOR]. Adding [COLOR=#DFDBD2][FONT=&quot]nameserver "8.8.8.8"[/FONT][/COLOR] into [COLOR=#E5E1D8]resolv.conf[/COLOR] also didn't help.

My syslog says the following:
[ATTACH=CONFIG]282627[/ATTACH]


So, it seems to boil down to the problem that the DHCP client does not accept the IP address offered by the router. 

I would be glad if anyone has an idea how to fix this and safe me from reinstalling my OS.

---

