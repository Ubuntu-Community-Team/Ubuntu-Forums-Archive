---
title: "sudoers and root | change username issue"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by saeeddeep on 2009-07-05
Hi all;
Q.1- My Ubuntu 8.04 box has only one user (username: user) with a sudo password (p@ss) this username/password is created during Ubuntu installation process.
How to add a new user account(admin) with a password (Newp@ss) and prevent the user(user) from using sudo command.
(i.e; 
     - Current State: "user" can invoke sudo using the password (p@ss) to run any command as a root.
     - Desired: "user" will NOT be able to invoke sudo command. A new user account(admin) with a password(Newp@ss) can run commands as root using sudo command and password of (Newp@ss).
) ... ?

Q.1- what is the bad results of running:
$ sudo usermod -l admin user
<I asked how to change root username, And the answer was # usermod -l <newname> <oldname>; but someone recommended not to change the root username, bacause this will lead to different problem ... ?

Thanks in advance...

---

### Post by Celauran on 2009-07-05
System -> Administration -> Users and Groups -> Add User. Be sure to add "Administer the system" in User Privileges tab. Log in as new user, go back to Users and Groups, remove "Administer the system" from original user.

---

### Post by CatKiller on 2009-07-05
Don't create a user called "admin". It won't work.

The admin group is one of the ways to control which users can gain administrative privileges. Creating a user with this name will attempt to create a group of the same name, which won't work, and then everything will break.

You also don't want to change the user name of root. Root is called root for a reason. Changing that name is just begging for everything to break.

Just use the Users and Groups tool to create a new user and give that user permission to administer the system. As an optional step you can subsequently remove those permissions from the first user.

Use sensible user names, such as the name of the user. Don't choose one of the names that are already in use. For example, calling the second user one of *root*, *audio*, *admin*, *pulse-rt* would be quite a daft thing to do.

---

### Post by saeeddeep on 2009-07-06
Thanks Celauran;
this is exactly what I want to do.

> **CatKiller said:**
> Don't create a user called "admin". It won't work.
The admin group is one of the ways to control which users can gain administrative privileges. Creating a user with this name will attempt to create a group of the same name, which won't work, and then everything will break.

Yes, you're right, Thanks.

---

