---
title: "Can't add anything to panels."
date: 2010-06-01
forum: New to Ubuntu
---

### Post by stevepoppers on 2010-06-01
I found an old thread with this title. First I tried
```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```
which did nothing. Then
```
sudo debconf gnome-panel
```
which allowed me to manipulate the panel in the normal way, but only while that process was running.

The old thread was solved by creating a user. That new user could manipulate the panels, then for some reason so could the old user.

Can I get a permanent fix? Using Lucid, if it matters.

EDIT: Nevermind. Logged out and back in. It all works now.

---

