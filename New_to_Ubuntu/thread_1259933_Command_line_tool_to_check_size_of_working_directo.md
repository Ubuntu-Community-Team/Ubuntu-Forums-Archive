---
title: "Command line tool to check size of working directory?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-09-06
Hi!  Is there a bash command to check the size of the current working directory.  For example:

travis@ubuntu-server:/var/spool/squid$<instert command I am looking for>
/var/spool/squid takes up 8.9MB

Anything kind of like that?  That would be way easier than using Disk Usage Analyzer to scan my server's entire filesystem via SSH just to see the size of my squid cache. . .

---

### Post by PGScooter on 2009-09-07
try du:

```
man du
```

for example, I use this a lot for the working directory:
```
du -sh ./ 
```

that will sum up everything in the working directory and then present it in human readable form (ie with k, m).

---

### Post by pi.boy.travis on 2009-09-07
AWESOME!!!  Thanks!

---

