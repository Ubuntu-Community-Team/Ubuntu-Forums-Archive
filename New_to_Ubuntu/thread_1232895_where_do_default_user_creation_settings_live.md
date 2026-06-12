---
title: "where do default user creation settings live?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by shawnisalk on 2009-08-06
Hey, there.

I've done some browsing in /etc but was unable to find where the default settings for user creation live.

When I set up the system, it created the first user with a handful of directories under /home/username. It set permissions, group membership, etc...

Can anyone tell me where those default settings live, or where  the script lives that performed that task?

I'd like to do it all manually and then possibly write my own script to automate it.

Thanks!:D

---

### Post by apjone on 2009-08-06
> **shawnisalk said:**
> Hey, there.

I've done some browsing in /etc but was unable to find where the default settings for user creation live.

When I set up the system, it created the first user with a handful of directories under /home/username. It set permissions, group membership, etc...

Can anyone tell me where those default settings live, or where  the script lives that performed that task?

I'd like to do it all manually and then possibly write my own script to automate it.

Thanks!:D


Open a terminal and run the following command.
```
man useradd
```

This should give you everything you need.

---

### Post by Cheesemill on 2009-08-06
When you create a new user the default directory is copied over from /etc/skel

---

### Post by ptn107 on 2009-08-06
You should be using **adduser** as opposed to **useradd**.  **adduser** is more friendly.  Defaults stored in '/etc/adduser.conf'.  (If you still want **useradd** defaults they are in '/etc/default/useradd'.

---

### Post by shawnisalk on 2009-08-06
Excellent! Thanks to all of you!

---

### Post by shawnisalk on 2009-08-06
ptn107--How do I mark the thread Solved?

---

### Post by ptn107 on 2009-08-08
Can't right now, it has been disabled.

---

