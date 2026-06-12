---
title: "Network is extremely slow even after disabling ipv6"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Jeffrey04 on 2008-04-14
I have just received the pc this morning for my new job and it comes with gutsy gibbon. However the internet connection is horribly slow that I cant do anything practical except browsing the internet. The installation of LAMP stack took me nearly one full working day...

I have tried prepending openDNS addresses to the dhclient.conf and the connection seems to be improved slightly. Then i went further to disable the ipv6 but there is no significant improvement to the connection speed.

Is there other information I would have to supply?

I have heard that the harddisk has some bad sectors.. could it be the cause of problem?

I was trying to download a copy of codeigniter but it fails all the time before I can finish downloading it.

---

### Post by bLaCkMeTaLL on 2008-04-14
maybe your resolv.conf is wrong ?

```
cat /etc/resolv.conf
```

---

### Post by Jeffrey04 on 2008-04-15
> **bLaCkMeTaLL said:**
> maybe your resolv.conf is wrong ?

```
cat /etc/resolv.conf
```

^.^"
the problem is solved.... it was caused by some configuration settings in the switch....

---

