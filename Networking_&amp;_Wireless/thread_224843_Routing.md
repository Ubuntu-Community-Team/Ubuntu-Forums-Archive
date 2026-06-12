---
title: "Routing"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by SigmaX on 2006-07-28
Yo;  I'm trying to set myself up a firewall on another computer, but I'm new to routing on UNIX and it's feeling a bit hectic.

I [think] I have the firewall comp setup properly as a gateway between my 10.0.0.0 network and 192.168.1.0 network.  Right now I just want to test it (It's FreeBSD, so I won't bother talking about the gateway-end here), and so I did the following on my Ubuntu client (Which is on the 10.0.0.0 network):

```
sudo route add -net 192.168.1.0 netmask 255.255.255.0 gw 10.0.0.1
```

The command executes and all seems well, but when I run "netstat -r" the entry I just tried to add does not show up, and the only system I can ping on the network is still 10.0.0.1.

Help?

SigmaX

---

