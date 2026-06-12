---
title: "Sharing/permissions problem"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by poisonborz on 2011-03-01
Hola,

Here is the situation:
In my /var/www folder (through ISPConfig) I have several folders, some are created with different owners (the website folders that ispconfig creates).
I have loaded this folder with "mount --bind" to my home directory on a different mount point.

I have chrgrp-ed the folder so that I can read/write all its contents through nautilus or ssh.

But: when I browse my shared Home folder, and try to open the mounted /var/www, I can't acces the folders that have different owners.

---

