---
title: "userdir permission issues with samba ad joined domain user / firefox and chrome(snap)"
date: 2024-11-29
forum: Networking &amp; Wireless
---

### Post by landjalan on 2024-11-29
hi there, 

i joinded my companies domain with samba, everything works well. when i use a windows ad domain user i can login with ad credentials a user directory is created and i can start using ubuntu.

but when starting firefox i see something like this:

```
~$ firefox
cannot create user data directory: /home/mydomain/mydomainuser/snap/firefox/4336: Permission denied 
```

the folder 4336 has the same permission as all other files created in /home/mydomain/mydomainuser/. i can create files, add content, setup my environment. except for firefox that i can not start. even the damned edge browser runs fine.

i encounter a similar error when launching chrome:

```
~$ chromium
cannot update snap namespace: cannot expand mount entry (none $HOME/.local/share none x-snapd.kind=ensure-dir,x-snapd.must-exist-dir=$HOME 0 0): cannot use invalid home directory "/home/mydomain/mydomainuser": permission denied
snap-update-ns failed with code 1
```


any ideas ?

---

### Post by Holger_Gehrke on 2024-11-29
That might be down to both Firefox and Chromium being snaps. AFAIK snaps can't access network shares. Your best option is to install either browser from a PPA (there is an official PPA by Mozilla and I wouldn't be surprised if there was something similar for Chromium).

Holger

---

### Post by landjalan on 2024-11-29
i dont like this workaround at all. that would mean for all software that is being offered as a snap i have to use PPAs ? the whole idea of snap would be destroyed. there must be another fix/workaround/solution.


and btw the refered folders are no network shares. these are local folders with external user/groupnames. like domainuser1:domaingroup1. only snap refuses to write in them. other tools do work fine.

---

