---
title: "Can't figure out my superuser...."
date: 2010-10-28
forum: New to Ubuntu
---

### Post by denneyjd on 2010-10-28
I'm a very extreme absolute beginner, but I'm trying to learn and I'm starting with MySQL.  I'm trying to execute a command that to change the directory of the files I downloaded for mysql, but it requires using the su - command.  I'm the only user on this computer and I've never taken it anywhere to get worked on and I can't for the life of me remember the password that it asks for.  I actually don't think I ever even set one.  Any ideas on how I overcome this?  Please keep it simple and in english because I'm still learning.  Thanks!

---

### Post by snowpine on 2010-10-28
There is no "superuser" or "root account" in a default install of Ubuntu (it is locked for security reasons). Instead, we use 'sudo' before a command to execute that command (and that command only) with root priviledges. The password is your regular, user password.

Here is more info:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

