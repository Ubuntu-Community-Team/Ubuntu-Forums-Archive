---
title: "NetworkManager 0.6.5"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by jellystones on 2007-04-27
[http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/)

I was browsing around on the NetworkManager FTP site looking for updates and found version 0.6.5 (Feisty Fawn comes with 0.6.4).

Anyway I am having similar problems to many people here with regards to wireless working only when NetworkManager is removed.

Anyway I was wondering if you guys would recommend upgrading manually, or should I just wait until an automatic update is provided through Update Manager?

---

### Post by spd106 on 2007-04-27
It's incredibly unlikely that there will be a version bump for network manager, only security fixes will be issued now.

It will be tricky to build it yourself as there are many dependencies and lots of modifications made to allow it to work with network-admin. Remember that NM is developed primarily for Red Hat which has a different networking structure to Debian based distros such as Ubuntu. I think your best bet would be to wait for Debian Unstable  update their version or perhaps Gutsy repos to open and then attempt a backport.

It's not something I've attempted, so it may turn out to be easier than that.

---

### Post by jellystones on 2007-04-27
Ok thanks, this is the answer I was looking for

---

