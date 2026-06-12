---
title: "super slow ssh logins and scp"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by professor-g on 2007-07-18
building yet another cluster for quantum chemical computations
8 nodes : core 2 duo (2.13 GHz), 4GB RAM in each
doing it all alone this time (without usual help from knowledgeable others - so need some help)
decided to go with Ubuntu this time (vs. regular Debian or sometimes Free-BSD)
installed openssh-server
commented out the following in /etc/ssh/ssh_config :

#    GSSAPIAuthentication yes
#    GSSAPIDelegateCredentials no

QUESTION 1: 
should I comment them out, or just set them both to 'no'
---
modified nsswitch.conf file as per some advice I found in others' posts
/etc/nsswitch.conf file looks as such for master node (server) :

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
#hosts:          files dns

/etc/nsswitch.conf file looks as such for slave nodes :

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns

QUESTIONS 2:
-should I be using the 1st (commented out, above) or 2nd instance for 'hosts:' ?

QUESTIONS 3:
- should master and slave nodes have same settings for /etc/nsswitch.conf ?

Please advise.
Thx,

G.

---

