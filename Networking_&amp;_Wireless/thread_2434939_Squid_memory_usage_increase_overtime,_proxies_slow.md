---
title: "Squid memory usage increase overtime, proxies slows down"
date: 2020-01-13
forum: Networking &amp; Wireless
---

### Post by buffdud on 2020-01-13
[COLOR=#000000][FONT=Verdana]Hello guys[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Running squid on ubuntu 16[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]When I first start the program, the proxies are at a good speed (below[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]100ms)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]after about 5 mins then memory usage of squid increases greatly, then the[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]proxies slow down to 1000ms+[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]my access log is getting spammed by the follow message ( I have no idea what[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]this means) I dont have a user named kaiz9n9d9[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]1578959115.266      0 216.115.184.251 TCP_DENIED/407 4130 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 kaiz9n9d9 HIER_NONE/- text/html[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1578959115.270      0 216.115.184.251 TCP_DENIED/407 4020 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 - HIER_NONE/- text/html[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1578959115.272      0 216.115.184.251 TCP_DENIED/407 4130 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 kaiz9n9d9 HIER_NONE/- text/html[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1578959115.276      0 216.115.184.251 TCP_DENIED/407 4020 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 - HIER_NONE/- text/html[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1578959115.277      0 216.115.184.251 TCP_DENIED/407 4130 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 kaiz9n9d9 HIER_NONE/- text/html[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1578959115.281      0 216.115.184.251 TCP_DENIED/407 4020 CONNECT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]www.supremenewyork.com:443 - HIER_NONE/- text/html[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]Currently I am running "service squid reload", every 300 seconds which keeps[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]the proxies at a good speed[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]But this is not a permanent fix

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]When I first start squid memory usage is around 24mb, then after 5 mins[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]increased to 1GB![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Also, the access log size increases by 500 kb every second, so I have[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]disabled access log for now[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Can someone please offer your advise for this issue?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks![/FONT][/COLOR]

---

### Post by wildmanne39 on 2020-01-13
Hello and welcome to the forum.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by SeijiSensei on 2020-01-14
First, where is this Squid installation running? Is it on a gateway of some sort with a public-facing IP address?  What address is 216.115.184.251?  Is it yours?  It doesn't have reverse DNS resolution set up. 

It looks like your proxy might be configured to accept requests from outside addresses like 216.115.184.251. Is that correct? If so, I'd take care of that first. In squid.conf you should have an acl that defines your internal network, and an http_access rule that limits access to the addresses in that acl.
```

acl localnet mynetwork 192.168.50.0/24
http_access allow mynetwork
http_access deny all

```
Does this machine have a firewall like a set of iptables rules? If so, it must be allowing external connections to port 3128. That's not good either. I'd remove whatever rule permits that from your iptables ruleset. In fact, I'd review your entire ruleset to make sure only authorized connections from external IP addresses are permitted.

---

