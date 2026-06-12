---
title: "Using nmblookup with firewall on"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by nutubu on 2005-05-12
In Samba, nmblookup is useful to find the current IP address of a Windows machine but it fails when the firewall is enabled.

The problematic packet is the NetBIOS Name Service answer from the Windows machine which comes back with the protocol UDP with source port 137 and a variable destination port(actually the port that was opened by nmblookup).

The way I fixed this was to add the following rule:

```

iptables -I INPUT  -p udp --sport 137 -s <my local network IP/mask> -j ACCEPT

```

Maybe there is a way to tighten the rule with the --dport switch but I don't know the possible range. I've seen packets coming back at ports around 32828 as well as 1023.

I hope this will be useful to someone.

Please post any better rule.

---

