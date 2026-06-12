---
title: "IP addresses for repositories and all other downloads"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-05
[B][SIZE="3"][COLOR="Magenta"]Hello,
[SIZE="3"]
Does anyone know where I can find the IP address list for ALL repositories and file / package sources?

(NOT URL's)[/SIZE]

I need to UNBLOCK the sites in our firewall and it can ONLY understand numeric IP addresses


Thanks[/COLOR][/SIZE][/B]

---

### Post by sdennie on 2009-02-05
The IP addresses will vary by your location.  Your firewall won't be blocking DNS requests so, you can just use nslookup to find the IP address of everything in your /etc/apt/sources.list.  For example:

```

nslookup security.ubuntu.com

```

---

