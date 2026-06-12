---
title: "Read-Only Disk?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Alpha C on 2009-10-30
I'm planning on changing to Windows again, simply because I need to be able to run a few programs for school.

I am trying to bring some of my pictures and music and other files with me, so was looking around for things to transfer them with. I found the disk I used to install ubuntu, so I figured I would put it in, delete everything on it, and fill it with my crap.

Little did I know it was protected by the godly read-only filesystem. Is there no way to just delete everything on a disk? Help would be greatly appreciated.

---

### Post by falconindy on 2009-10-30
If by disk you mean CD, then yeah... of course it's read only.

---

### Post by fancypiper on 2009-10-30
CDs and DVDs are read only by their nature, so unless it is a R/W disk, you can't change it.

To erase a r/w disk:
sudo cdrecord dev=<cdburnerdevice> blank=all

This will wipe a drive of all info:

dd if=/dev/zero of=/dev/<your drive here>

---

