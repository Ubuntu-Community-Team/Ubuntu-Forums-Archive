---
title: "Restricting http access from 2 IP's?"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by spcoex on 2007-09-01
hi all, 

how can i restrict inbound access to my http server to only two ip addresses (from my home and from work, both static IP's)? 

I know iptables is enabled by default and that it can easily be configured with firestarter...BUT, the only instructinon I see are for a GUI and I want to use a command line. What file do I edit?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall)


Thanks

---

### Post by kidders on 2007-09-02
Hi there,

Assuming your iptables INPUT chain is configured to drop (or otherwise disallow) incoming packets by default, you could remove the rule that is admitting HTTP traffic at the moment, and replace it with a set of per-IP rules, perhaps along the lines of...```
iptables -A INPUT -i eth1 -p tcp --dport http -s 12.34.56.78 -j ACCEPT
```

As you rightly imply, there's very little point in dirtying your server with a firestarter/similar install. There's plenty of iptables documentation around though, which I would recommend you read some of, before altering your firewall. General iptables concepts are the same across all platforms, so it doesn't really matter whose documentation you read.

[SIZE=1]_**Important note:**_
This may not apply to you at all, but please be aware that it is not appropriate to use iptables as a substitute for authentication. If the web server you are protecting exposes sensitive information that you are seeking to protect, you *must* supplement your iptables rules with good-quality authentication.
[/SIZE]

---

