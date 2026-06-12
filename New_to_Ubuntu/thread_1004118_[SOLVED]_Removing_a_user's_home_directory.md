---
title: "[SOLVED] Removing a user's /home/ directory?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-06
I created a user using:
```
useradd username
```
The purpose of this user is so that I can add it to the sambashare user group so that this user can access my samba share on a WinXP machine.

I later found out that by default this creates a /home/ directory for the user and also allows the user to login to my Ubuntu box locally as well as via SSH.  To correct the login issue I simply issued the following command:
```
sudo usermod -s /sbin/nologin username
```
So now 'username' can't login locally or via SSH :D
But the user still has a /home/ directory :(
How can I get rid of the /home/ directory for that user ('username') ?
TiA,
-BassKozz

---

### Post by drs305 on 2008-12-06
> **BassKozz said:**
> How can I get rid of the /home/ directory for that user ('username') ?


If you want to delete all traces of the user, do the following. If you just want to delete the home folder, see the next post.

System, Administration, Users & Groups. Unlock, highlight the user, Delete.

Or (be careful):
```

sudo deluser --remove-home *[COLOR="DarkRed"]username.to.delete[/COLOR]* # removes home folder and mail spool
*or:*
sudo deluser --remove-all-files *[COLOR="DarkRed"]username.to.delete[/COLOR]* # removes all files of user on system

```

---

### Post by lykwydchykyn on 2008-12-06
Get admin privileges, and just delete it.  At the command line, that'd be:

sudo rm -Rf /home/username

---

### Post by BassKozz on 2008-12-06
Thanks drs305...
> **lykwydchykyn said:**
> Get admin privileges, and just delete it.  At the command line, that'd be:

sudo rm -Rf /home/username
lykwydchykyn,

Won't the system still think the user has a /home/ directory even thou it's been deleted?

---

### Post by BassKozz on 2008-12-06
> **drs305 said:**
> If you want to delete all traces of the user, do the following. If you just want to delete the home folder, see the next post.

System, Administration, Users & Groups. Unlock, highlight the user, Delete.

Or (be careful):
```

sudo deluser --remove-home *[COLOR="DarkRed"]username.to.delete[/COLOR]* # removes home folder and mail spool
*or:*
sudo deluser --remove-all-files *[COLOR="DarkRed"]username.to.delete[/COLOR]* # removes all files of user on system

```
I just issued:
```

sudo deluser --remove-home *[COLOR="DarkRed"]username.to.delete[/COLOR]*
```
and it completely removed the user (not just the home directory :(

Also when I go in and try and remove the home directory from _S_ystem>_A_dministration>Users and Groups I get the following error message: [IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/users-admin-remove-home.png[/IMG] :(

Any other way to do this?

---

### Post by lykwydchykyn on 2008-12-07
> **BassKozz said:**
> Thanks drs305...

lykwydchykyn,

Won't the system still think the user has a /home/ directory even thou it's been deleted?

I suppose so, but since they can't log in that's a tad irrelevant. I suppose if you want to you can open your favorite user management tool and change the home directory to /dev/null, though I'm not sure what that will do to samba.  Is the only purpose of creating this user to create a samba account?

EDIT:  it seems making the home directory /dev/null is the preferred approach, from some checking I did.

---

### Post by BassKozz on 2008-12-07
> **lykwydchykyn said:**
> EDIT:  it seems making the home directory /dev/null is the preferred approach, from some checking I did.

Thanks **lykwydchykyn**,
You mind telling me your checking? What source?
Just curious
Thanks again,
-BassKozz

---

