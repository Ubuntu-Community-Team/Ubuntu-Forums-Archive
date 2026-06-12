---
title: "one host blocked after 48hours"
date: 2020-12-04
forum: Networking &amp; Wireless
---

### Post by raoul-markus on 2020-12-04
Hi, 

I have a strange issue with my home network. My raspberry zero can't reach my home server after ~2 days of normal operation. When I reboot the server, it works again. 

only the connection between these two is broken. Other clients with similar software reach the server. Normally this server is up like 50-100 days without issues. The zero can ping/reach all other ips in the network. 

So my assumption is that something on the server is blocking the connection to the zero after some time. I have browsed through the syslog.. checked iptables.... AFAIK I don#t have any firewall running on the server (which would be the first thing to look for if it would be windows). 

Any idea what I could look for?


Network layout:
fritzbox <-> ethernet to server (ubuntu 14.04.5)
fritzbox <-> wlan to zero (rasbian 10)

Thanks, 

Best regards,

---

### Post by CelticWarrior on 2020-12-04
Ubuntu 14.04 is EOL since April 2019. Please install a supported release.

There's no point in troubleshooting an obsolete release.

---

### Post by raoul-markus on 2020-12-14
ok. For this and other reasons, I upgraded the server. Since bananapi does not provide any newer ubuntu, I had to change hardware. It is now a small AWOW PC with a celeron. 

Now with Ubuntu 20.04 server the observed issue no longer appears.

---

