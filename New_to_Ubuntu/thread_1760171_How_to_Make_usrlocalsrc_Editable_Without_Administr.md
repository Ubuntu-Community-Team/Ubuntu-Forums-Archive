---
title: "How to Make /usr/local/src Editable Without Administrator Rights"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-05-16
Ok, so I store all my source code/non-deb programs in /usr/local/src. It's nice because I always know where to put stuff and where to find it without taking up space in my home folder. But I can only edit the contents of it when I use kdesudo dolphin (or my custom launcher). So how do I make it so I can make changes to the contents of this folder without putting my password in every time? I tried the commands in the documentation about compiling source code, but that didn't help.

---

### Post by mikewhatever on 2011-05-16
You should assign the ownership of the folder and its contents to yourself.
```
sudo chown -R USER:USER /usr/local/src
```

---

### Post by compmodder26 on 2011-05-16
Assuming you are the only user that accesses /usr/local/src, you could do the following in a terminal:

```
sudo chown -R <your username> /usr/local/src
```

replace <your username> with the username of the user you log in with.

This will make /usr/local/src, as well as all subdirectories/files owned by you.

---

### Post by dniMretsaM on 2011-05-16
Awesome thanks guys!

---

