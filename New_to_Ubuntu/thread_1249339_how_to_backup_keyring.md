---
title: "how to backup keyring"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Shpongle on 2009-08-25
i want to format my system and reinstall a minimal install or try crunchbang, is there a way to backup my keyring , so i can use it when i reinstall?,

---

### Post by isparkes on 2009-08-25
In general, all of the settings are held in hidden files in your home directory. (Hidden means that they start with a ".").

You can fairly easily backup ALL of your settings by just preserving the home directory, e.g. using tar:

```
tar tvf home-backup.tar /home/<yourname>
```

---

### Post by Shpongle on 2009-08-25
thanks but i know that, i only wanna keep the keyring tho, iv all my other stuff backed up, my system has gotten so sluggish, so i figure it was all the messing around i did with it, so i want it fresh again:) , but i need to have the keyring codes

---

### Post by winotree on 2009-08-25
Is what you're looking for to be found in **/home/user/.gnome2/keyrings** ??  My file contains **default**, **default.keyring** and **login.keyring**.  ;)

---

