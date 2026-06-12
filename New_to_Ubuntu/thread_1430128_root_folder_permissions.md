---
title: "root folder permissions"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Fika on 2010-03-15
Is it normal to not have permission to open or edit the root folder? I don't recall seeing this as locked in other installs of ubuntu. I am running apparmor in enforce mode if that makes a difference.

---

### Post by Enigmapond on 2010-03-15
Yes absolutely normal.

---

### Post by ndefontenay on 2010-03-15
For a longer answer:

Only your home folder /home/[username] allows you to edit create or delete files.

You won't be able to edit a file in root unless you use the sudo command. Which elevate your session as root for the duration of whatever you want to do. A password will be required when sudo is used.

---

