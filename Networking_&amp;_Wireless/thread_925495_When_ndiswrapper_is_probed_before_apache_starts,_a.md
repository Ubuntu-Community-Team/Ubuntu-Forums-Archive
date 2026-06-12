---
title: "When ndiswrapper is probed before apache starts, apache will hang and take down gnome"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by obscenic on 2008-09-20
Installed ndiswrapper and apache2/php5/mySQL.

With ndiswrapper NOT in /etc/modules:
Computer starts fine, I can sudo modprobe ndiswrapper and everything works like a charm.

With ndiswrapper IN /etc/modules (or in a startup script etc):
Gui login appears, login works, but before nautilus or gnome panels are visible, a gnome settings daemon error appears.  System hangs before OK can be clicked.  CTRL-ALT-BACKSPACE shows apache attempting to start, and system becomes fully unresponsive.

Any ideas?  Manually loading ndiswrapper is not really acceptable, as this is a point of sale/member management server in a bike co-op :)

---

### Post by obscenic on 2008-09-29
Bump.

---

