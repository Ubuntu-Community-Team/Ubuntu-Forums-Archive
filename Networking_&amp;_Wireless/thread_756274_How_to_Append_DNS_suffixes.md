---
title: "How to Append DNS suffixes"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by kooldino on 2008-04-15
First off, don't bother direcetly editing resolv.conf, as it will be overwritten at boot time.

```
sudo vi /etc/dhcp3/dhclient.conf
``` (feel free to use your editor of choice instead of vi)

and then remove the "#" from the supersede line and add in whatever DNS suffixes you'd like (space delimited):

```
supersede domain-name "blah.joe.schmoe fun.toe.joe.schmoe";
```

Hope this saves someone some time.

---

