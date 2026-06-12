---
title: "Internet Connected; but Firefox deos not load webpages"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by rahimveron on 2007-10-08
I am using rp-pppoe to connect with ADSL modem. I have installed pppd connection through ```
pppoeconf
``` command.
The problem is sometimes while surfing using Firefox or Opera, i suddenly am not able to connect to any site, the status bar continue to indicate "Looking for ...."message. Funnily, my Deluge is fine and is able to download as well as upload during this error.
Here are the contents of pon dsl-provider:
```
## Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
usepeerdns
user "myusernae@isp"
```

/etc/hosts:
```
#127.0.0.1 localhost SEBA
127.0.1.1 SEBA

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

hostname:
```
SEBA
```

Further my connection also hangs quite frequently if i leave it idle fr 10 minutes.

---

### Post by rahimveron on 2007-10-10
Bump....
Help me yaar

---

