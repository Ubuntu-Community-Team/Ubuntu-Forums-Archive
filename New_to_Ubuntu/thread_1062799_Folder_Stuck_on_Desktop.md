---
title: "Folder Stuck on Desktop"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by jondska on 2009-02-07
I was playing a cd a friend sent me with some wav files on it and now there is a folder on the desktop of 8.10 that says Audio Disc.volume and it won't go away. I try to move it to the trash and it just stays there. When I click on it it says: "x-nautilus-desktop:///Audio%20Disc.volume". How do I get rid of it?

---

### Post by billgoldberg on 2009-02-07
```
rm -rf /home/yourusername/Desktop/folder
```

replace it with the name you log in with and the exact name of the folder

Be sure to specify that exact folder or it will delete more than you want.

---

### Post by Achetar on 2009-02-07
Or, if the directory is empty do this:
```

rmdir ~/Desktop/folder

```

Replace folder with the folder you want to erase.
rmdir will not erase directories that have files in them. You will have to use billgoldberg's tip for that.

---

### Post by jondska on 2009-02-07
Thank you. Things are so simple when you know what you're doing.....

---

