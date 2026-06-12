---
title: "Not in sudo list?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by littlegreenman on 2009-02-02
Hello,

in the process of configuring my ubuntu machine to share the /dev/sdb1 drive in the network I installed samba, and created all the ubuntu users for each windows user that would be accessing the drive.

This is all being done from user littlegreenman, which is my username and the username from wish I sudo.

In the end I realised I had to add an admin account as well, because all windows computers have an admin account, all with the same password, and sometimes we might need to access the drive /dev/sdb1 from within the admin account.

So i created a login admin.

A few minutes later littlegreenman was not in the sudo files anymore, and admin was.

I never said ok to this switch. 

Now I was trying to access the Users and Groups administration option, and when I click on Unlock, the system never asks me for a password and returns an error saying: an unexpected error occurred.

(Sorry if this is not exactly what it says. My ubuntu is in Portuguese, so I am translating here)

So now I have two problems,

1 - I want littlegreenman to be sudo again. I want Admin not to be sudo.
2 - I cannot access the users and groups option.

If could show me how to do this in the command line, that would solve my first problem. I don't know how to do it.

But it would be also cool to fix the error i get when trying to access the users and groups option.

Thank you very much for all the help :-)

Diogo

---

### Post by zvacet on 2009-02-02
There was no need to make new admin user.During installation of Ubuntu you created admin user (littlegreenman I believe) and password for it.What you  can do now?Maybe somebody will come with better idea but here is my suggestion;

boot in recovery mode and type

```
adduser littlegreenman admin
```

After restart you will be able to go to the users&groups and there remove admin you created,so only user with admin privileges wil be littlegreeenman.

---

### Post by sisco311 on 2009-02-02
When you create a new user in ubuntu the system creates a new group with the same name. I think this is the problem. What's the gid of the admin group in ubuntu? 

Edit: BINGO!! bug:[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305")

---

### Post by littlegreenman on 2009-02-02
> **sisco311 said:**
> Edit: BINGO!! bug:[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305")

OK, so here is what I tried from that site:

> I just messed up a fresh xubuntu 8.04.1 install by creating an "admin" user. It should be blocked in some way.

The 'Users and Groups' gui tool got broken and pressing 'unlock' resulted in a non-descriptive error message. admin users no longer had 'administer the system' checked, though they could still use sudo at the terminal.

I fixed (well it seems fixed as far as I can see) this by creating a new admin user:

adduser newadminuser
adduser newadminuser admin

then logging out of the "admin" user and changing to the newly created user then removing the "admin" user using:

deluser admin

After this the gui tools worked again.

The difference was that instead of creating a new user I did

adduser littlegreenman admin

logout

login littlegreenman

deluser admin

littlegreenman now has sudo previleges, but I still cannot access the GUI for users and groups.

Going to reboot the system to see if that changes anything.


EDIT:

Rebooting did the trick. I now can access the GUI for users and groups, and can use it no problem.

BEWARE of ADMIN!

---

