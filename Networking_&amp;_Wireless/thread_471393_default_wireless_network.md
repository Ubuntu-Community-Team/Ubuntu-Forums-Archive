---
title: "default wireless network"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by eweibust on 2007-06-11
There are two wifi networks that are always available from my house, my network and my neighbors.  For reasons, unknown to me, my neighbors wifi network is the one that my laptop connects to when I boot.  How can I change this?

I running a very standard install of Ubuntu 7.04.

Thanks...
Erik

---

### Post by spd106 on 2007-06-12
You may find this wiki page useful [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Specifically section 8.

---

### Post by eweibust on 2007-06-12
Awesome.  Using that gconf-editor did the trick.

Erik

---

### Post by Peter Chastain on 2008-01-12
What if 'system->networking' doesn't appear in gconf-editor?  Any suggestions?

Thanks.

-Peter

---

### Post by mstrymn on 2008-01-12
don't run as sudo.

just ```
gconf-editor
```

not ```
sudo gconf-editor
```




should help some.

---

