---
title: "Where is the samba config file"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Frozen Forest on 2011-08-14
It's possible with Ubuntu to select a folder in the home folder and share that folder, but where is the config file for these shares? It don't seem to be the general config file for samba at '/etc/samba/smb.conf'

---

### Post by Enigmapond on 2011-08-14
I believe the path would be:

```
**/etc/samba/smb.conf
```**

---

### Post by spiky001 on 2011-08-14
Are you looking for right click folder select sharing options???

---

### Post by Frozen Forest on 2011-08-14
> **Enigmapond said:**
> I believe the path would be:

```
**/etc/samba/smb.conf**
```

> **spiky001 said:**
> Are you looking for right click folder select sharing options???

I'm looking for the config file where those folders that are shared is stored. Let say I decide to share the 'Music' folder, where is this setting stored. If the computer is restarted is the music folder still shared so it has to be saved somewhere, it isn't in '/etc/samba/smb.conf' since root access is never requested so no write access to that file. I know that it's possible to write into smb.conf that a folder should be shared.

EDIT:
It might be the config file for gnome-user-share that I'm looking for

---

### Post by coffeecat on 2011-08-14
> **Frozen Forest said:**
> 
It might be the config file for gnome-user-share that I'm looking for

It is. The configs for nautilus or gnome shares are in /var/lib/samba/usershares .

---

### Post by Morbius1 on 2011-08-14
Not to nitpick but gnome-user-share is the package that brings you "Personal File Sharing" which has nothing to do with Samba. Nautilus-share is the package that creates share definitions at /var/lib/samba/usershares.

It's unfortunate that the name gnome-user-share was chosen.

---

