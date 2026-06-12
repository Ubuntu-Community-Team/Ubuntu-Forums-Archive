---
title: "root user authentication failure"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by khatikbbdn72 on 2010-12-12
hie, 
i am newbie.. hope u guys could help me out..

i try to use command "su" to login as a root user...
but when i enter my password .. it pops up with autentication failure..
i am the only user of my ubuntu.. and i use the same password that i used at the time of system installation, another problem that comes through.
when i add user using "useradd" command..
it adds the user but it is not shown in my default home directry

plz help

---

### Post by coffeecat on 2010-12-12
> **khatikbbdn72 said:**
> i try to use command "su" to login as a root user...

Not in Ubuntu. have a read of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by khatikbbdn72 on 2010-12-12
what about other question.. directory or path name of directory wher i can see all the user name of the system..?

---

### Post by coffeecat on 2010-12-12
You need the -m option to create a user home directory if you use useradd. See man useradd. But why do it the hard way? Go to System > Administration > Users and Groups.

Which distro have you been using up until now? :)

---

