---
title: "Some help with creating users with no permissions"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by CharlesA on 2009-10-15
Hi all,

I don't want to mess with security settings (just yet) so that I can create users using the GUI on Ubuntu Server. However, I am wondering if there is a way to set the user group so that they don't have any way to login.

When I created a few users before throwing my server in a corner with no keyboard/mouse/monitor, I was able to create users from gnome using the Users and Groups command. There was an option to create a user with no permissions.

Is this possible to do from the command line, and if so, how would it be done?

I've already set those those users to use /dev/null for both the home directory and the shell.

Hope this makes sense.

Thanks in advance!

---

### Post by yknivag on 2009-10-15
Creation of users is done using the command
```
sudo useradd username
```
This will create a locked user who will have no access.

```
sudo passwd -l username
```
will stop an existing user from logging in and/or getting a shell.

You can then (re)activate them (if required) by changing the password.
```
sudo passwd username
```

---

### Post by CharlesA on 2009-10-15
> **yknivag said:**
> Creation of users is done using the command
```
sudo useradd username
```This will create a locked user who will have no access.

```
sudo passwd -l username
```will stop an existing user from logging in and/or getting a shell.

You can then (re)activate them (if required) by changing the password.
```
sudo passwd username
```

Thanks!

I thought that would lock me out of accessing Samba shares with those account names. Apparently not. 

:)

---

