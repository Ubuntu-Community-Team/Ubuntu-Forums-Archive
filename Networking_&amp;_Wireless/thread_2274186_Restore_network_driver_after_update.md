---
title: "Restore network driver after update"
date: 2015-04-18
forum: Networking &amp; Wireless
---

### Post by duchesnen on 2015-04-18
I am running Ubuntu Server 14.04 LTS on a Dell D830 with a Broadcom NetXtreme 57xx Gigabit Controller as the wired interface.

Since I ran the last update (sudo apt-get dist-upgrade) the network drive doesn't load anymore (no more eth0 interface).

I have a _network_ backup available, made with rsync.

I plan to boot the server with a USB key to start a live session and restore what I need from the backup.

1) Is it the best way to recover from this problem?
2) What do I need to recover (directories / files)?  I am not familiar about how ubuntu stores its drivers.
3) Is there special permissions issues that I need to be aware of, since the restore will be made by a different user than the backup?
4) What could I do to prevent this problem from re-occuring?

Thank you.

---

### Post by oldos2er on 2015-04-18
Moved to Networking & Wireless.

---

