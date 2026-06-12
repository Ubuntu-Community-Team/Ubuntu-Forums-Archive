---
title: "How to create an auto save command for a file ?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by ubfu on 2010-06-13
I wanted to create an auto save command as for backup on a certain file.
Such as .sqlite files.
Creating something like a simple bash command to backup it every 3 hours or everyday 12 hours.
Is it possible to do that ? 
Thank you

---

### Post by arrange on 2010-06-13
Where do you want them to be backed up to?
I use a simple *cron* job and ```
find -type f -iname '*.sqlite' -cnewer $TimestampFile
```

---

### Post by slash86 on 2010-06-13
It's not a command, but can be usefull for you.
Have you ever tried sbackup??? it is availabe in synaptic. You can configure various folders and it will do a backup for you based in your configuration. By the way, i'm quite sure it uses cron.

---

