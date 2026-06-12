---
title: "Log the console"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by foppeh on 2010-03-10
I'm about to perform a series of operations on the console. I want to log input/output to file so I can look at some actions and results lateron.
Is the console already logged on file? I can't find it in /var/log/. Else, is there a solution, preferrably as a setting so I won't have to pipe to file and remember not to forget that part ;)

Thanks

---

### Post by marshmallow1304 on 2010-03-10
You can use script for that.
```
script logfile.log
```
and
```
exit
```
to stop the log.


See
```
man script
```
for more info.

---

### Post by foppeh on 2010-03-10
Cool, thanks. That's about hat I was looking for.

---

