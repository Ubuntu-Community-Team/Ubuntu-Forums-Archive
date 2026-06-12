---
title: "dpkg"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by mbemarkt on 2010-09-23
Sorta newbie here - I'm trying to upgrade to 10.04 and it keeps shutting down @ 95%... something to do with dpkg?  HELP!

---

### Post by drs305 on 2010-09-23
Welcome to the Ubuntu forums!  :-)

Are you upgrading from 8.04 or 9.10? 
On-line or a clean install?]
If online, which method are you using (what command if in terminal)?

I know it might be hard to do, but if possible it would be useful to get to get the exact error message.

Did you do an upgrade of all your packages on your old Ubuntu release before trying to upgrade to 10.04? Any error messages when you run
```
sudo apt-get update
```
in your old release?

---

### Post by mbemarkt on 2010-09-23
I tried to update yesterday and received a dpkg error message as well - that's why I attempted to install 10.04 from a live CD (upgrading from 8.04).  I can't recall the exact message but said I needed to configure dpkg mannually.

---

### Post by mprice on 2010-09-23
Sounds to me like it said to run:

```
sudo dpkg --configure -a
``` which should fix the problem.

---

