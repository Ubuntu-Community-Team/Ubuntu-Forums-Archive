---
title: "[SOLVED] copying group membership"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by lazyart on 2009-01-08
Joined my machine to my windows domain with Likewise.  Authentication works great.  Users who log in really have no permissions.

I'd like to copy the group permissions from the first created user to my own, so that I can administer the machine from my domain account.  Is there an easy to do this?  I can use id to fetch my user id... just want to easily add that id to the same groups as user id 1000.

Thanks.

---

### Post by lazyart on 2009-01-09
Found my own solution.

```
gksudo gedit /etc/group
```
Did a search for the initial user, replacing it with the initial username, followed by a comma and my domain name:

"lazyart" became "lazyart,MYDOMAIN\\domain_user_name"

Rebooted just to be sure and now I have access.

---

