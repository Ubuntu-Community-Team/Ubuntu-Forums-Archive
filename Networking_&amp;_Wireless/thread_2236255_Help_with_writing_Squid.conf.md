---
title: "Help with writing Squid.conf"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by **FuSeD** on 2014-07-25
Hey :)

I need some help writing the config for my proxy, I'm just getting a bit confused with how it all works.

I have it setup for a transparent proxy.

What I wanna get working is for the the proxy to block all ports except those used to access the internet, preferably I would like to block https as well. Also I would like to block access to certain websites to stop access to bad sites like porn and stuff lol. I wanna keep the default block page the squid uses too lol.

Any help would be awesome :) I'm in well over my head here.

---

### Post by SeijiSensei on 2014-07-25
Blocking outbound traffic uses **iptables**.  If you want a transparent squid proxy, you'd need rules like these (assumes eth0 points to Internet and eth1 to local network):

```

/sbin/iptables -A INPUT -i eth1 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp  --dport 80 -j REDIRECT --to-port 3128
/sbin/iptables -A INPUT -i eth1 -j REJECT

```

First rule allows HTTP traffic, which the second rule pushes through Squid.  Third rule blocks everything else from the local network.

---

### Post by **FuSeD** on 2014-07-25
Hey thanks for the reply,

I have ```
post-up iptables-restore < /etc/iptables.up.rules
``` in the /etc/network/interfaces file and in the iptables.up.rules file I have ```
*nat

-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.2.10:3128
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
-A POSTROUTING -s 192.168.2.0/24 -o eth0 -j MASQUERADE
COMMIT
``` I'm not sure how I would amend this file with the code you gave me, I'm still a noob when it comes to Ubuntu :)

---

### Post by SeijiSensei on 2014-07-25
Try deleting the first PREROUTING rule.  Does that help?

DNAT rewrites the packet's outbound address with 192.168.2.10.  I don't think you want that.  The second rule, like the one I gave you, pushes HTTP traffic that would go out eth1 through the Squid proxy.  I take it your gateway has the opposite configuration from the one I posited.  Looks like your eth1 points to the Internet, while eth0 points to the local network.

---

### Post by **FuSeD** on 2014-07-25
Got it, I made a typo in the networking file wasn't connecting. :) typed "init" instead of "inet". Just gotta figure out how to block sites now.

---

### Post by SeijiSensei on 2014-07-25
Create an acl in squid.conf like this:
```
acl banned_domains dstdom -i "/etc/squid3/banned_domains.conf"
```
then include this http_access declaration above the final rule that permits general access
```
http_access deny banned_domains
```
Create a file /etc/squid3/banned_domains.conf with each domain on a separate line. Reload the configuration file with "sudo squid -k reconfigure".

You can ban URLs as well as sites and create ACLs with a wide variety of other keys.  I use regular expressions for most rules, but string matching works as well.  The parameter dstdom matches domains by string, but you can use dstdom_regex to use regular expressions.  I'd start by reading [http://wiki.squid-cache.org/SquidFaq/SquidAcl](http://wiki.squid-cache.org/SquidFaq/SquidAcl).

---

### Post by **FuSeD** on 2014-07-26
Awesome thanks :)

---

