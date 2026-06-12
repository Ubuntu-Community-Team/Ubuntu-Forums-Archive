---
title: "Does logrotate create error logs?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by purvez on 2011-06-08
Please can someone tell me if logrotate creates a log of any errors it encounters.  If 'yes' then where is this file kept.

One of my logs is not getting rotated on the production machine but does on the development machine and I can't see any differences in set up so I'm trying to find out what might be happening.

Thanks

Purvez

---

### Post by dargaud on 2011-06-08
try running it by hand with -d and -f

---

### Post by purvez on 2011-06-08
Thanks for your quick response.  Since it's a production machine and I only support my app on it, I'm a bit reluctant to run it in case I muck up other stuff.  Can I run logrotate manually for a particular file only?

Purvez

---

