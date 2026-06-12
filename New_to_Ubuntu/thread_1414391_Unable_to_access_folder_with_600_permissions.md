---
title: "Unable to access folder with 600 permissions"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by dj_bridges on 2010-02-23
I know that this is basic stuff, but am relatively new to using Ubuntu. Basically I created a folder with 600 permissions ie only the user can read and write to it, but even though I am the user and the group owner I can't access the directory. Am i missing something really obvious???

dan@Sammy:~$ ls -l
drw-------   2 dan dan 4.0K 2010-02-23 20:25 TEST
dan@Sammy:~$ cd TEST/
bash: cd: TEST/: Permission denied

---

### Post by vanadium on 2010-02-23
A directory must have the execute permission.

---

### Post by wojox on 2010-02-23
You want 700 permissions.

---

### Post by mcduck on 2010-02-23
like other mentioned, you also need the execute permission to be able to list the directory's contents (or cd into that directory).

Read permission only allows you to access files inside the directory (if you know the full path to the file).

---

### Post by dj_bridges on 2010-02-24
Thank you everyone for putting me right on that front. I knew it was going to be obvious to someone in the know, but couldn't find anything about it when searching.

Hope this helps someone else who doesn't understand this at first!

:popcorn:

---

