---
title: "[SOLVED] /etc/host.conf and /etc/hosts files"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2008-05-18
Hello Everyone,

I've been pulling my hair out trying to figure out if the trouble is me or COX cable.
Do these look correct???

host.conf
```
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
```hosts
```
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
#
#        My Setup
#
127.0.0.1 localhost localhost
70.173.236.4    ubuntubox.hobby-site.org localhost
```Thank You,
Barrie

---

### Post by dmizer on 2008-05-19
site works for me.

three links: ubuntu blog, hvac login, and nhra blog

do you have a router with loopback capability (most likely not)?  if not, you'll have to point your /etc/hosts to your local machine loopback like so:
```
127.0.0.1 localhost
127.0.1.1 servername ubuntubox.hobby-site.org

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

for all the clients on your network, you'll need to update the hosts so it points to your server's local ip like so:
```
127.0.0.1 localhost
127.0.1.1 clientname
[COLOR="Blue"]192.168.1.x[/COLOR] ubuntubox.hobby-site.org

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
* change [COLOR="Blue"]192.168.1.x[/COLOR] to reflect your server's actual local ip address.

---

### Post by Barriehie on 2008-05-19
Thank You Dmizer,  I appreciate your rapid response and code examples! :)

Barrie

---

