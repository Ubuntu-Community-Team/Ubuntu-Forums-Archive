---
title: "iptables-persistent rules,accept ssh only from specific ip addresses"
date: 2015-12-08
forum: Networking &amp; Wireless
---

### Post by zeusys on 2015-12-08
[FONT=arial]Hi.
I want to write some rules in [/FONT][FONT=monospace][FONT=arial][COLOR=#000000]/etc/[/COLOR][/FONT][COLOR=#000000][FONT=arial]iptables[/FONT][FONT=arial]/rules.v4 to accept ssh only from some [/FONT][FONT=arial]ip[/FONT][FONT=arial] addresses. But the server should accept traffic on other ports from any [/FONT][FONT=arial]ip[/FONT][/COLOR][FONT=arial][COLOR=#000000] address.

How should I write rules to do that?

Thank you
[/COLOR][/FONT]
[/FONT]

---

### Post by ian-weisser on 2015-12-08
One good way is at [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by SeijiSensei on 2015-12-08
```
/sbin/iptables -A INPUT -p tcp -s 10.10.10.10 --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s 10.10.10.11 --dport 22 -j ACCEPT
[etc.]
/sbin/iptables -A INPUT -p tcp --dport 22 -j REJECT

```

You can use CIDR subnet addresses like "10.10.10.0/24" as well as host IPs.

---

