---
title: "diskdump between 2 pcmcia compact flash cards (virtual disks)"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by fabloub on 2010-08-23
Hello,
I have a debian distribution installed on a compact flash card that I would like to copy onto another one. I have a laptop running ubuntu 8.04 that has two pcmcia slots. I tried:
dd if=/media/disk of=/media/disk-1
but it seems that I can't use dd on the folders.

What should I do in this case?
Thanks.

---

### Post by fabloub on 2010-08-23
I am now trying dd if=/dev/sdc of /dev/sdb
I think it's working but it's very slow.

---

### Post by fabloub on 2010-08-23
Yep that worked.

---

