---
title: "locate doesn't work for normal users - and a fix"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by wizard10000 on 2009-04-26
I'm a big fan of locate but it doesn't work for normal users in Jaunty because the permissions on /var/lib/mlocate/mlocate.db are set to 640 instead of 644.  I chose to change the database permissions instead of adding myself to the mlocate group.

Bug #367313 submitted.

:)

---

