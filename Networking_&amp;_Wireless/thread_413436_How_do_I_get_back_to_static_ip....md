---
title: "How do I get back to static ip..."
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by master5o1 on 2007-04-19
I can't access the network-admin thing in any way (comman line or gui) and I want to set my wireless up for static instead of dhcp.

What should I have in my /etc/networking/interfaces file?

[code]
auto wlan0
iface wlan0 inet dhcp
wireless-essid *****
wireless-key *****
[/code[]

So what should this become?

---

### Post by sisco311 on 2007-04-19
> auto wlan0
iface wlan0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
wireless-essid *****
wireless-key *****
with xxx.xxx.xxx.xxx replaced by your settings, of course

---

### Post by master5o1 on 2007-04-19
thanks.

---

