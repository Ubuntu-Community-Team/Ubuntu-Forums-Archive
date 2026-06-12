---
title: "Create New User in Root Group with Maximaum Permissions"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by AvocadoNia on 2008-12-14
How do I create a user with maximal permissions in the root group?
I am using Intrepid 8.10. 


Thank you.

---

### Post by inxygnuu on 2008-12-14
What do you mean? There is only 1 root, but you can create another admin account As Far As I Know. (AFAIK8))

---

### Post by drs305 on 2008-12-14
?.  If you want a user with most privileges, open System, Administration, Users & Groups. Unlock (with sudo password), Add User, fill out the Account Info and in the Privileges tab check as many as you need/want.

---

### Post by AvocadoNia on 2008-12-14
> **inxygnuu said:**
> What do you mean? There is only 1 root, but you can create another admin account As Far As I Know. (AFAIK8))
Thank you. Yes, I need to create a user that has adminitrative permissions.

---

### Post by AvocadoNia on 2008-12-14
> **drs305 said:**
> ?.  If you want a user with most privileges, open System, Administration, Users & Groups. Unlock (with sudo password), Add User, fill out the Account Info and in the Privileges tab check as many as you need/want.
Thank you. System>Administration>Users & Groups...

I get this message
The configuration could not be loaded
You are not allowed to access the system configuration

Maybe there is another way?

---

### Post by drs305 on 2008-12-14
You must have administrative (root) privileges to be able to add a user. Can you use 'sudo' and know the password?

The other way to add a user if you have root privileges is 1. via the command line or 2. boot to the recovery mode, select "boot to root prompt". In in the command line ( substitute the new user name you want for *newuser* ) :
```

sudo adduser *newuser*
sudo adduser *newuser* admin

```

Note: If the above is done from the admin group, you do not need to include 'sudo'.

You would probably want to add other groups for the new user. You can run "groups" in a terminal to see what groups you belong too and might want to add. Or, if you can get it to work, via the Privileges tab in Users & Groups.

---

