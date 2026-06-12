---
title: "question about setting IPv6 address and default gateway"
date: 2021-07-26
forum: Networking &amp; Wireless
---

### Post by wingpig001 on 2021-07-26
Hey,

I am setting IPv6 address on my computer like this ```
[COLOR=#37474F][FONT=Menlo]sudo ip -6 addr add [/FONT][/COLOR][COLOR=#2695EE][FONT=Menlo]2408[/FONT][/COLOR][COLOR=#37474F][FONT=Menlo]:8509:1880:3526:1695:7f07:d3bc:c307/128 dev tun_srsue[/FONT][/COLOR]
```. After this, when I setting default gateway ```
[COLOR=#37474F][FONT=Menlo]sudo ip -6 route add default via [/FONT][/COLOR][COLOR=#2695EE][FONT=Menlo]2408[/FONT][/COLOR][COLOR=#37474F][FONT=Menlo]:8509:1880:3526:1695:7f07:d3bc:c307 dev tun_srsue[/FONT][/COLOR]
```, it reports "Error: Gateway can not be a local address." How can I solve this? Many thanks!

---

### Post by ximera on 2021-08-01
The address ending c307 is presumably one given to you for your machine.  You should also have been given a different address for the gateway - possibly fe80::1.

---

