---
title: "PYTHON: how to find the newest file in a directory and open it with cat"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by leahk on 2010-07-07
i am trying to first identify the last file added to the directory and then open it with cat.


r=commands.getoutput('ls -ct1 | head -1')

print r

os.system('cat r')



if i wrote os.system(cat 'name of file') it works but not with the variable

??

---

### Post by da burger on 2010-07-07
I'm not a python programmer so I can't solve your problem but I can tell you what's wrong.

Because 'cat r' is in quotes python reads it as literally that. It doesn't substitute in the variable. You need to find the "python way" to add the string stored in r to "cat ".

Angus

---

### Post by DaithiF on 2010-07-07
Hi,
i'm not going to ask why you're using python in this way, ie. as a wrapper around shell commands, rather than just using shell commands themselves, or indeed, using pure python.  Assuming theres a good reason for doing it this way, then:

```
os.system('cat "%s"' % r)

```

also the admins here frown on double-posting, ie posting the same question in multiple forums, so they'll probably merge these threads when they notice.
[http://ubuntuforums.org/showthread.php?t=1526010](http://ubuntuforums.org/showthread.php?t=1526010)

---

### Post by leahk on 2010-07-07
k that works but its printing out the pyc not py

---

### Post by DaithiF on 2010-07-07
> **leahk said:**
> k that works but its printing out the pyc not py

ok.  though i'm not sure if you're asking a question here or just making an observation.

---

