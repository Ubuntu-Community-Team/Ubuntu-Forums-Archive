---
title: "No user accounts after minimal"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mrbiggbrain on 2009-06-11
I was installing the minimal ubuntu install on my pendrive and overlooked something, user names and passwords.

now when i go to boot at the login screen i dont have any boot passwords, is there still a way i can go and get a user account set up?

---

### Post by kerry_s on 2009-06-11
select the second option at grub to boot into failsafe mode.
run> **adduser**

---

### Post by mrbiggbrain on 2009-06-11
> **kerry_s said:**
> select the second option at grub to boot into failsafe mode.
run> **adduser**

i installed lilo, grub had an issue.

---

### Post by rockerphil on 2009-06-11
you've got 2 options i can think of. first is to reinstall and DON'T forget the user name & password, or you can boot it in to recovery mode (thus accessing a root shell) and adding a user using the "adduser" command, although the only problem with that is that sudo won't work in that account forcing you to log in to root to do any administrative tasks thus defeating the Ubuntu security framework. hope this helps,

Phil

---

