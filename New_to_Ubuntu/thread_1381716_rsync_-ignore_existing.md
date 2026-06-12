---
title: "rsync -ignore existing"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-01-15
Hi

I've implemented an rsync backup in cron for our office - my query relates to the use of the "ignore existing" variable.

If I use it does the backup skip archiving a file if a file of the same name already exists on the destination, regardless of other parameters (i.e. size, last modified date etc).

Any help would be appreciated.

Cheers

---

### Post by duanedesign on 2010-01-20
I think you are correct 'man rsync' reads as:

--ignore-existing       skip updating files that exist on receiver

---

