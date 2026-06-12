---
title: "need to know nano command"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-04
Hi,

I'm going to make a backup file in grub thus:

nano cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

what is the procedure to install the backup if i rm  the original?

Thanks

---

### Post by realzippy on 2009-11-04
To "load" backup:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf



To make a backup:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

---

