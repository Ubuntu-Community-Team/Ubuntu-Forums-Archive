---
title: "Going batty...package installer and corp firewall"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by NoOne2 on 2007-12-11
I'm behind a corporate firewall at work.  For the package installer to work properly I need to get out on the internet.

I've configured the proxy for the proper setup but it still does not even seem like its trying.

All my other apps work fine when I can configure them for each application.  

Doesn't package installer use the system proxy?

Thanks

---

### Post by mpokrywka on 2007-12-11
Package installer do not use "system proxy" (I guess you mean proxy settings in Gnome/KDE) because installer must work even if there is no desktop environment.
Connection settings are stored in /etc/apt/apt.conf file (create if it doesn't exist).
To use http proxy add settings:
```
Acquire
{
    http
    {
        Proxy "http://127.0.0.1:8080";
    };
};
```
Of course insert your proxy ip/port. If your proxy needs authentication check:
zless /usr/share/doc/apt/examples/configure-index.gz
for instructions.

---

