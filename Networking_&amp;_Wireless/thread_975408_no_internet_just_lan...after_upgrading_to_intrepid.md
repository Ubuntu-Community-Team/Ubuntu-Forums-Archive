---
title: "no internet just lan...after upgrading to intrepid"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by overblue on 2008-11-08
so i had hardy upgraded it to intrepid and when i try to connect to any host out of my lan it can't connect..
dns works...(because the dns server is in the lan)
flushed iptables...
i don't know how to get this one...

some of the errors i got while booting are
ifup can't open state file because it's read-only filesystem
and cp can't write a file in a read-only filesystem

fstab line for /
UUID=49d66ff8-53c0-4f0b-ab9d-1dff7a509e73 /               ext3    rw,defaults,errors=remount-ro 0       1

i also tried to boot with errors=continue
and in grub booted with rw but no changes..

---

### Post by overblue on 2008-11-08
bump

---

