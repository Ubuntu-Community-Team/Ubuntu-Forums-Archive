---
title: "Network admin-&gt; connections: No add button?"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by dontpanic0 on 2006-11-01
In the connection tab of 'network-admin' there is no add or delete button, so I can't configure wlan0 to work.  Could someone please help me fix this?

---

### Post by dmizer on 2006-11-01
well, this is one of the biggest shortcoming of relying on gui as your source of information, because i can't figure out what you're referring to.  this is not to say that what you're trying to do can't be done with a gui, it simply means that without direct visual reference, i really can't tell what you're looking at.

my best suggestion to you is to edit interfaces directly like so:
```
gksudo gedit /etc/network/interfaces
```
and edit your wlan0 according to your needs.

---

