---
title: "ping doesn't resolve FQDN"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by cerdiogenes on 2007-04-23
Hi,

I connected to my university network through DHCP and when I try to ping something I get:

ping: unknown host [www.google.com.br](www.google.com.br)

I edit the file /etc/hosts to:

127.0.0.1 localhost
127.0.1.1 carlosd-laptop

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

and ping again google and everything worked fine. Can someone explaim me the reason for this.

Thanks,
Carlos.

---

### Post by matthewmceachen on 2007-04-26
This may be a side-affect from an issue with avahi-daemon: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/98763]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/98763"). Change this line in your /etc/nsswitch.conf 
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
to be
```
hosts:          files dns
``` 
and resolution should work again (but note that avahi resolution will be broken). 

You could also try uninstalling avahi.

---

