---
title: "Is it possible to backup the casper-rw file?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by crob26 on 2011-04-22
hello! i am currently running ubuntu 10.10 off of my USB with a 1.1 GB  persistence file. If i were to backup the casper-rw folder, and  reinstall ubuntu on my USB, and paste the persistence file from before  on the flash drive, would all my persistent files and settings be on the  new ubuntu i installed? thanks.

---

### Post by oracle2b on 2011-04-22
I'm not sure if you'd be able to mount teh capser-rw upon boot. I've mbeen able to mount the casper-rw under live mode to backup my /home directory.

create a folder 'casper' on the desktop(or any where you want)

> sudo mount -o loop /cdrom/casper-rw /home/*insert username*/Desktop/casper

---

