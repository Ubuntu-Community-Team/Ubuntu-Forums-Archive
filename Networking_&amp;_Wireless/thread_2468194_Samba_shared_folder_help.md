---
title: "Samba shared folder help"
date: 2021-10-20
forum: Networking &amp; Wireless
---

### Post by fjl05 on 2021-10-20
What combination of parameters do I need to make a service/folder where authorized users (no guests) can enter and be able to add files and folders. Where everyone can read each others files and folders but no one can delete or modify anything except the user/owner that put it in there?

---

### Post by TheFu on 2021-10-21
The way to have different permissions in Samba is to have different shares for the different types of access rights.
Samba ignores Unix permissions, but will set them as requested. So ... 
a) owners which are the only userid with write to the files, would have 1 share with full rights
and 
b) non-owners which have to be in either an approved list or a normal Linux group, would have another, read-only, share.

[https://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-TABLE-2](https://www.samba.org/samba/docs/using_samba/ch08.html#samba2-CHP-8-TABLE-2) has a list of different permissions that can be applied to a share.

This is a common pattern, BTW. I've never seen a more elegant way, but perhaps someone will post a different solution.  I'm not a fan of any *force user* or *force group* options in business settings.  There should be a userid tied to each file that relates back to an individual.  In a home environment - go crazy - do whatever works for you, but there are risks.

---

### Post by Morbius1 on 2021-10-21
See how far this example gets you:

```
sudo mkdir /srv/Shared
sudo chown root:plugdev /srv/Shared
sudo chmod 3775 /srv/Shared
```

```
[Shared]
    create mask = 0644
    force directory mode = 03775
    force group = plugdev
    path = /srv/Shared
    read only = No
    valid users = tester smbuser
```

*** tester and smbuser can access the share.
*** tester and smbuser can write to the share.
*** tester and smbuser can read each others files
*** neither user can delete or edit a file or subdirectory created by the other.

EDIT: There's no real reason why I chose to use pludev as the group.

---

### Post by TheFu on 2021-10-21
> but no one can delete or modify anything except the user/owner that put it in there? 
How does this get accomplished?

---

### Post by fjl05 on 2021-10-22
> **Morbius1 said:**
> See how far this example gets you:

```
sudo mkdir /srv/Shared
sudo chown root:plugdev /srv/Shared
sudo chmod 3775 /srv/Shared
```

```
[Shared]
    create mask = 0644
    force directory mode = 03775
    force group = plugdev
    path = /srv/Shared
    read only = No
    valid users = tester smbuser
```

*** tester and smbuser can access the share.
*** tester and smbuser can write to the share.
*** tester and smbuser can read each others files
*** neither user can delete or edit a file or subdirectory created by the other.

EDIT: There's no real reason why I chose to use pludev as the group.


What are 4 digit chmod commands? Where can I find info on this?

Also it works! thanks!
Now if only I can figure out how and why it works...

---

