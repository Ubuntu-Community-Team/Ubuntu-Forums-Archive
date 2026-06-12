---
title: "can not play movie from samba share"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by karl_kashofer on 2007-10-18
Ok, I know there is lots of threads about this, but I do not get it:

Here is the situation:

I have a samba share on a feisty box and try to play movies from a second feisty box. I use Konqueror, doubleclick the movie and Kaffeine complains about something like missing plugin.

The smb.conf of the box i try to play from has
guest ok = no
if I set that to 
guest ok = yes
it suddenly works....

I do not understand why kaffeine is not able to access the file after I logged into the share with konqueror. Obviously I cant leave guest access enabled.

Anyone here to help ?

Thnx,
Karl

---

### Post by mpokrywka on 2007-10-18
Probably this is some kaffeine bug, maybe credentials are not "passed" from konqueror... I say ditch this crappy VFS...
This will always work and with all (kde/gnome/console) apps:
```
mount -t cifs //server/share your_dir -o user=username 
```
You need to have "smbfs" package installed, also check **man mount.cifs** how to supply password (you may pass via command line, or via file), or how to set permissions if they are wrong...

---

