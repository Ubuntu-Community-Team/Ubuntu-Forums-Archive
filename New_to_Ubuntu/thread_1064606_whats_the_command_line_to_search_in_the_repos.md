---
title: "whats the command line to search in the repos?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-02-09
I want to upgrade my transmission bittorent.

I typed in:

```
sudo apt-cache search transmission
```

and found a list transmissions which are:

```
transmission-common - free, lightweight BitTorrent client
transmission-gtk - free, lightweight BitTorrent client (graphical interface)
transmission - free, lightweight BitTorrent client
transmission-cli - free, lightweight BitTorrent client (command line interface)

```

whats the command line to found out which versions are offer?

---

### Post by adult swim on 2009-02-09
try ```
sudo apt-cache policy transmission
```

---

### Post by Voland on 2009-02-09
```
apt-cache show *package_name*
```
For futher information use ```
man apt-cache
``` ;)

---

