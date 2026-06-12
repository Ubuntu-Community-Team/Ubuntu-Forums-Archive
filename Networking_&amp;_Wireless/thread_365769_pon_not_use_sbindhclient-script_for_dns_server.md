---
title: "pon not use /sbin/dhclient-script for dns server ?"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by xport on 2007-02-20
Hi...buddies, I have some question about pon and dhclient-script !

for the normal ADSL dial-up, we run the following command:
```

shell> pon dsl-provider

```

but I notice that the man says:
> 
a  PPP connection will be started using configuration from /etc/ppp/peers/provider.  This is the default behaviour unless an isp-name argument is given.


so I do some changes as the following:
```

shell> sudo cp /etc/ppp/peers/provider /etc/ppp/peers/provider.ubuntu
shell> sudo cp /etc/ppp/peers/dsl-provider /etc/ppp/peers/provider
shell> pon   #notice: here run without the 'dsl-provider'

```

my ADSL dial-up scuessfully...but I meet another issue on my DNS server, the resolv.conf file had been rewrited. 

But I had comment out the 'make_resolv_conf' in /sbin/dhclient-scripts.

if I use 'pon dsl-provider', the resolv.conf leave unchanged.
if I use 'pon', the resolv.conf was rewrited.

it seems that runing 'pon' only dont's go with /sbin/dhclient-scripts.

Anyone can tell me what happend ? thanks. :confused:

---

### Post by xport on 2007-02-20
Ahh...I'm still waiting your help...!

---

