---
title: "Is it possible to alias a hostname?"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by jmillikin on 2007-05-27
Is it possible to create a hostname alias? Sort of like /etc/hosts, but with other hostnames rather than IP addresses. So that with some file like this, you could ping "fakehost1", and it would be re-mapped to "realhost", and then "realhost" would be resolved to an IP address.

```
# Real host        # Aliases
realhost           fakehost1 fakehost2 fakehost3
```

---

### Post by hronir on 2007-11-14
if your main issue is not to ping but to ssh, you can create/edit your ~/.ssh/config adding lines like these:

Host fakehost1
Hostname realhost

Host fakehost2
Hostname realhost

Host fakehost3
Hostname realhost

Cheers,

---

