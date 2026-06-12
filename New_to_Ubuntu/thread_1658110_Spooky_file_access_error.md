---
title: "Spooky file access error"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by loldrup on 2011-01-02
Yesterday my friend's computer started to behave weird in relation to file writes:

When she want to write to an existing file using an application (we have tried meld, bzr extmerge and aptana studio) it didn't change the file on the harddrive... no warning was given. She tried with gedit once, and that worked, mysteriosly.

We wanted to examine the problem, so we tried changing directory to a folder witch she has read and write access to, but then we got a permission error:

```

julie@laptop:~/bachelorprojekt/repo/trunk/src/src$ ls -l
total 440
-rw-rw-rw- 1 julie julie  1784 2010-12-31 12:59 clock.pyc
-rw-rw-rw- 1 julie julie  3756 2010-12-31 15:09 dataTypes.py
-rw-rw-rw- 1 julie julie  4051 2010-12-31 15:21 dataTypes.pyc
drw-rw-rw- 2 julie julie  4096 2010-11-15 15:56 deprecated
-rw-rw-rw- 1 julie julie  1612 2010-12-31 12:55 dmCache.py
julie@laptop:~/bachelorprojekt/repo/trunk/src/src$ cd deprecated/
bash: cd: deprecated/: Permission denied
julie@laptop:~/bachelorprojekt/repo/trunk/src/src$ sudo su
root@laptop:/home/julie/bachelorprojekt/repo/trunk/src/src# cd deprecated/
root@laptop:/home/julie/bachelorprojekt/repo/trunk/src/src/deprecated# 
```

this is very weird as she clearly has the rights to access the 'deprecated'-directory.

---

### Post by Idefix82 on 2011-01-02
Actually, she doesn't have the permission to enter the directory. For that, you need the execute permission, but she only has read and write permissions. See e.g. [here]("http://articles.techrepublic.com.com/5100-10878_11-1047531.html") or [here]("http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions").

---

### Post by loldrup on 2011-01-02
Thank you!

Giving the owner and group execution rights also solved the problem with changing the files using an application.

---

### Post by Idefix82 on 2011-01-02
You are welcome. Can you please mark the thread as solved (under thread tools above the first post), so that other helpers here know not to divert their energy and others seeking advice know that it is to be found here.

---

