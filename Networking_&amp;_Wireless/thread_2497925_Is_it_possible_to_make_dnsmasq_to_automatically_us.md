---
title: "Is it possible to make dnsmasq to automatically use DNS servers provided by DHCP as u"
date: 2024-05-23
forum: Networking &amp; Wireless
---

### Post by mahany on 2024-05-23
[SIZE=2][FONT=arial][COLOR=#0C0D0E]I have dnsmasq configured to use upstream dns servers manually set with the option "server=" in "/etc/dnsmasq.conf". These upstream servers are used to resolved public ip addresses and domains.[/COLOR]
[COLOR=#0C0D0E]This machine gets its DNS servers list by DHCP and looks like this in resolv.conf file.
[/COLOR]```
nameserver 127.0.0.1
nameserver <upstream1>
nameserver <upstream2>
search <domain-name>
```

[COLOR=#0C0D0E]Here is also the content of the file "/etc/resolvconf/interface-order"
[/COLOR][/FONT][/SIZE]```
[FONT=arial]lo*
[/FONT][SIZE=2][FONT=arial]ens34*[/FONT][/SIZE]
[SIZE=2][FONT=arial]ens33*[/FONT][/SIZE]

```[SIZE=2][FONT=arial]
[COLOR=#0C0D0E]The DHCP is controlled by a different team and they may change the DNS servers at any time, I wanted to know if there is a way to tell dnsmasq to use the two upstream servers set by the DHCP server in resolv.conf instead of manually specifying the upsteam servers in dnsmasq.conf everytime the DNS servers IPs are changed by the networking team?[/COLOR][/FONT][/SIZE]

---

### Post by currentshaft on 2024-05-24
a b

---

