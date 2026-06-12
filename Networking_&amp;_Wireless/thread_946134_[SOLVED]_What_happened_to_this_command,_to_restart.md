---
title: "[SOLVED] What happened to this command, to restart networking???"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-10-13
What happened to this command?

> chuckdl@chuckdl-laptop:~$ sudo etc/init.d/networking restart
[sudo] password for chuckdl: 
sudo: etc/init.d/networking: command not found
chuckdl@chuckdl-laptop:~$ 

Any help on this one?

---

### Post by OutOfReach on 2008-10-13
try:
```
sudo /etc/init.d/networking restart
```

You forgot the first slash. ;)

---

### Post by buccaneere on 2008-10-13
> **OutOfReach said:**
> try:
```
sudo /etc/init.d/networking restart
```

You forgot the first slash. ;)

Thanks...

I was already tryin' to delete the thread... I haven't had any network problems for a long time, and forgot till I saw it...

---

### Post by OutOfReach on 2008-10-13
Happens to the best of us. :)

Make sure to mark your thread as solved: Thread Tools (Above your first post) >Mark thread as solved

---

