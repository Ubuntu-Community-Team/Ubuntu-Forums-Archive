---
title: "Changing root password."
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Jetso on 2010-11-07
How do you change the root's password, if it can be done. There is only one user on my computer. Since the user is Admin, is the password just always that? This is all in theory, I'm trying to learn more about Linux.

---

### Post by chaanakya_chiraag on 2010-11-07
By default, the root account is not enabled and you should use sudo to do all admin tasks.  That said, you can always do a ```
sudo passwd root
``` and enable the root account.

---

### Post by Joeb454 on 2010-11-07
On Ubuntu there's no real need to change the root password, as everything is done via sudo.

If you're the only user on that PC, the root password is essentially the same as your password, and you would prefix commands with sudo to run things as root, e.g. ```
sudo apt-get update
``` or ```
gksu update-manager
``` if you wanted to launch a graphical application

---

### Post by Jetso on 2010-11-07
I was confused I suppose, I thought sudo and root where the same thing. ](*,)

---

### Post by chaanakya_chiraag on 2010-11-07
Well sudo lets you do stuff as root, but without actually having to log in as root.  This means root can be disabled (to discourage hackers), but you can still do stuff as if you are root (using sudo).

---

### Post by M@N on 2010-11-07
Use this command in terminal window:

```
sudo passwd
```first type your password, then the new root password

---

### Post by Jetso on 2010-11-07
M@N : And that will change the password sudo asks for, but not my account?

---

### Post by ajgreeny on 2010-11-07
There is absolutely no need to enable the root password to do anything that a normal desktop user would need.
See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for all the detalis.

---

### Post by Jetso on 2010-11-07
Haha, thanks for all the help. This was all just theoretical anyway :P

---

