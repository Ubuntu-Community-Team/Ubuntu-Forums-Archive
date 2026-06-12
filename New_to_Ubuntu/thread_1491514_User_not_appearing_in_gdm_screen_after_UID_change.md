---
title: "User not appearing in gdm screen after UID change"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by doomrobo on 2010-05-23
Hi, I'm new to the forums. I just bought a Macbook Pro and after installing ubuntu, I wanted to view my OSX files. So I go into the folder in nautilus and lo and behold, I don't have the permissions. So I find out it belongs to UID 501 (my OSX user id) and I decide to change my ubuntu UID to match it so I can view them without having to play chown tug-of-war. After I change my UID with usermod, everything works except for my login screen. Now I can still log in, but I have to manually type in my username and then password instead of my username showing up in the gdm menu. Any help to fix this would be much appreciated.

---

### Post by pkilian on 2010-07-06
I had the same problem after changing my uid to match an LDAP account stored on my NAS box. It turned out to be a setting in the file /etc/login.defs.

Simply edit the the file (*sudo vi /etc/login.defs* or *sudo gedit /etc/login.defs*) and change the following from:

UID_MIN   1000
GID_MIN   1000

to:

UID_MIN   500
GID_MIN   500

Log out and you should see your user in the list.

---

