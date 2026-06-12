---
title: "Backup files but keep orginal premissions"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by White Horse on 2010-01-26
I need to backup files of  WEBserver but when i copy files and then copy them back (when i ruin database) my server says he don't have permission to files anymore, root is the only one with permission.

My question is how do I backup complete folder with preserved original permissions? What is commad?

---

### Post by freak42 on 2010-01-26
rsync has a flag to preserve permissions:

 -p, --perms                 preserve permissions

rsync is preferable for backing up anyhow as opposed to copy, methinks, you'll find plenty of useful tutorials using google.

hth

---

### Post by White Horse on 2010-01-26
Thank you very much.

Just needed some direction for google-ing :)

---

