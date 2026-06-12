---
title: "Adding the initial user to a group"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by SteelCore on 2010-08-25
I'm trying to set up a shared directory between the users on my computer. Using System>Administration>Users and Groups I created the group and ticked the names of all 3 users on the system, including myself. But when I use 'id' on the command line I don't see it under my groups although it appears for the other 2 users.
I created several groups in this manner with the same results.
Thanks for any help.

---

### Post by sisco311 on 2010-08-25
You have to log out and log back in for changes in group membership to take effect.

See:
```
info coreutils 'id invocation'
```

> Primary and supplementary groups for a process are normally inherited
from its parent and are usually unchanged since login.  This means that
if you change the group database after logging in, `id' will not
reflect your changes within your existing login session.  Running `id'
with a user argument causes the user and group database to be consulted
afresh, and so will give a different result.

---

