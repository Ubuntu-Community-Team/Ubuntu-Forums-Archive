---
title: "Can't delete files and folders"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Castor68 on 2009-04-14
I copied two folders with movies inside of them from a external device to the hard disk. Now, I can't delete them. In the Videos folder they are locked (the folder icon is with a lock on it). I tried changing the file permissions to read-write status to delete it later but it didn't work.

I have enough space in the hard drive but, I just know why I can't delete them.

Any ideas?

---

### Post by MegaJim on 2009-04-14
Probably due to the root user owning the file.

You can fix it by opening nautilus as the super user then browsing to the file and changing its owner by right clicking the file -> properties -> permissions and change the owner to your account.  Hit alt+F2 then type in

```
gksu nautilus
```

to open a root file browser, but be careful with it !

---

### Post by jbrown96 on 2009-04-14
They are probably owned by root, so even though you can read/write to them, you aren't allowed to remove them.

Try the rm command. ```
sudo rm /PATH/TO/VIDEOS
``` or if you want to remove the folders as well ```
sudo rm -rf /PATH/TO/FOLDER
```

If you don't want to get into the terminal, then you can use nautilus. Alt+F2 then gksu nautilus and enter your password.

---

### Post by Castor68 on 2009-04-14
**jbrown96**: I did as you said and it didn't work.

---

### Post by Castor68 on 2009-04-14
**Megajim**: it worked with Nautilus. I deleted them without problems.

Thanks a lot.

---

