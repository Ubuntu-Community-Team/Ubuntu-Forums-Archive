---
title: "Policy routing: “from” in routes"
date: 2019-08-19
forum: Networking &amp; Wireless
---

### Post by mariobidongalindez on 2019-08-19
[COLOR=#242729][FONT=Arial]I'm trying to understand what is the use of employing the "from" keyword in routes, as opposed to rules.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have two routes: default from 2001:470:aaaa::/48 dev ipv6-tunnel metric 100 pref medium default via 2001:bbb:ccc::1 dev eth0 metric 1024 pref medium[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]These rules were created with: /sbin/ip -6 route add default from 2001:470:aaaa::/48 dev ipv6-tunnel /sbin/ip -6 route add default via 2001:bbb:ccc::1 dev eth0[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And a packet that gets sent from the 2001:470:aaaa::/48 prefix ends up using the second default rule, as opposed to the first one, which is supposed to be more specific (in the sense that it specifies a "from" prefix).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]any clues?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]thank you![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]mario[/FONT][/COLOR]

---

