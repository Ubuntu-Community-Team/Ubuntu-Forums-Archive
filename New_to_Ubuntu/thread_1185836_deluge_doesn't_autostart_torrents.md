---
title: "deluge doesn't autostart torrents"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by JebusWankel on 2009-06-12
When I add a torrent to deluge, it remains in the queued state until I make it no longer auto-managed. How do I get it to download automatically?

---

### Post by lovinglinux on 2009-06-12
You need to increase the number of allowed active torrents in the Queue section of the preferences.

For example if you set the option "Total Active" to zero, then all your torrents will be added to the queue but won't start, unless you make them no longer auto-managed.

You should set the "Total Active" to a number that equals the number of torrents you want to be actively downloading at the same time, plus the number of torrents that will be actively seeding at the same time. For example, set the "Total Active" option to 3, then set "Total active downloading" to 2 and "Total Active seeding" to 1. So, if you add several torrents to the queue, you will always have 3 active torrents. Two will be downloading and one will be seeding.

---

