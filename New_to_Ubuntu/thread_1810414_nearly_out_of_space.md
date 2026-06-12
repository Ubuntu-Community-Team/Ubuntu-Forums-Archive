---
title: "/ nearly out of space"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Legeril on 2011-07-23
my / is nearly out of space, I got a warning today. I have only 500MB left, I did some checking around and I have over 60GB in var > log folder. I am wondering what is ok to delete and what isn't, it seems to be a very large number to be honest...

---

### Post by 3rdalbum on 2011-07-23
If it's in /var/log, you can safely remove all of it. Sounds incredibly large for a set of log files - see if there's one file that's massively large and then take a look to see if there's error messages printed in it over and over again. You might want to look into stopping whatever is printing those messages into the file, because it's probably taking up CPU time and disk I/O doing this.

---

### Post by mcduck on 2011-07-23
Actually 60GB in /var/log sounds like you have a problem on your system that causes some log file to fill with error messages and grow insanely large.

Before you delete anything there, you should check what log file(s) are that large, and take a look at the error messages. That way you can solve the actual problem, just deleting the log files would leave the problem alone and over time the log files would grow again.

(other than that, any of the log files are safe to delete. it's just that in this situation doing so wouldn't be much of help, kind of like trying to threat a broken leg with pain killers, it takes the symptoms away for a while but doesn't actually fix anything ;))

---

### Post by Legeril on 2011-07-23
OK I've taken a look at the files, and the ones that seem VERY large (like 9GB) are kern.log, ufw.log and sys.log - of these are are multiple. all the errors seem to be related to ufw in some way..

---

