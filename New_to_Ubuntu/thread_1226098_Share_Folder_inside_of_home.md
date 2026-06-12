---
title: "Share Folder inside of home"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by lake54 on 2009-07-29
What do I need to do to share my .VirtualBox folder with another user on the same computer? The existing one is a full user, whilst the one I want to be able to access it with is a standard user.

James

---

### Post by CatKiller on 2009-07-29
Probably just give that folder permissions for other users to access it, and then symlink that directory to the Home directories of each of the users that you want to use that directory instead of whatever they were using before.

---

### Post by lake54 on 2009-07-29
Thanks for that - I tried to do so, but it said it couldn't access (permission denied etc).

Is there a folder on Ubuntu that I can move the folder to so that both users can read/write to it? Similar to Shared Docs on Windows.

Actually, now I think about it, I could just move it to another hard drive - doh!

Thanks for your help

James

---

### Post by CatKiller on 2009-07-29
> **lake54 said:**
> Thanks for that - I tried to do so, but it said it couldn't access (permission denied etc).

Each user (probably) doesn't have permission to write inside another's Home directory. Root has permission to write in both. You can run the file manager as root with ```
gksudo nautilus
```Be careful with what you do when running things as root.

---

### Post by tarps87 on 2009-07-29
```
sudo mkdir /home/share
sudo chmod a+rwx /home/share
```

You may want to change the owner and group, also be careful if you create a user will the name share ;)

As so a folder in your area
```
chmod a+rw -R *folderToShare*
```

(You can right click and do this using on of the tabs)
[]

---

