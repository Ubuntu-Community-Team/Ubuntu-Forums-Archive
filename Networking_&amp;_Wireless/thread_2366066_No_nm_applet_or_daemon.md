---
title: "No nm applet or daemon"
date: 2017-07-13
forum: Networking &amp; Wireless
---

### Post by buntu_hugenewbie11 on 2017-07-13
I recently upgraded from 14.04 to 16.04.
I then used the xenial backports to get the more usable plasma.
Now the issue I have is that there is no network daemon or applet.
I cannot even tell which wireless network I am attached to via gui.
How do I get the applet up? Or at least some network application in the gui?
Or should I remove the xenial backport? Prior to this plasma version (on default 16.04) networks were showing. And an nm applet seemed to exist.

Details are here: [http://paste.ubuntu.com/25083194/](http://paste.ubuntu.com/25083194/)

---

### Post by vasa1 on 2017-07-13
> **buntu_hugenewbie11 said:**
> I recently upgraded from 14.04 to 16.04.
I then used the xenial backports to get the more usable plasma.
Now the issue I have is that there is no network daemon or applet.
I cannot even tell which wireless network I am attached to via gui.
How do I get the applet up? Or at least some network application in the gui?
Or should I remove the xenial backport? Prior to this plasma version (on default 16.04) networks were showing. And an nm applet seemed to exist.

Details are here: [http://paste.ubuntu.com/25083194/](http://paste.ubuntu.com/25083194/)
When you say xenial backports, was it via *ppa:kubuntu-ppa/backports*? That's what I used to move from the default plasma in 16.04 to plasma 5.8.7.

Re. not seeing the applet, is it possible that it's just hidden?

And if you run```
ps axjf
```do you see something like this:```

    1   833   833   833 ?           -1 Ss     106   0:10 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
    1   862   862   862 ?           -1 Ssl      0   0:00 /usr/sbin/ModemManager
    1   863   863   863 ?           -1 Ssl      0   0:09 /usr/sbin/NetworkManager **--no-daemon**
  863  1122  1122   863 ?           -1 S        0   0:00  \_ /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wl
  863  1155  1155   863 ?           -1 S    65534   0:00  \_ /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-fi
    1   867   867   867 ?           -1 Ssl      0   0:00 /usr/lib/accountsservice/accounts-daemon
    1   868   868   868 ?           -1 Ss       0   0:00 /usr/sbin/cron -f
  
```

---

