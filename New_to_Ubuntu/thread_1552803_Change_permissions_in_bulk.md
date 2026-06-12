---
title: "Change permissions in bulk"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by gallifrey on 2010-08-14
Hi all, 
        I have just downloaded a few icon themes, which for some reason were not working properly. After a little investigation, I found that permissions were set incorrectly on A LOT of the icons in question, i.e. set for root owner, group access:none, others access: none, so up to now, I have been checking each one manually, and setting it's permissions correctly.

I have tried changing permissions on the folder level, i.e. setting the folder permissions, and then clicking "apply permissions to files in folder", but it does not seem to affect the target files. 

Is there any way I can just blitz the whole lot so they all have the same permissions??

---

### Post by NightwishFan on 2010-08-14
Easiest way I found was this command.
```
sudo chown -R ***user*** ***/directory/tree***
```

---

### Post by Vaphell on 2010-08-14
chown -R  <user>:<group> <dir>

if i am not mistaken directories require executable bit enabled and you don't want that in case of files. if you require to change read/write/execute bits something along the lines of:

find <dir> -type d -exec chmod <permissions for directories> {}\; (755?)
find <dir> -type f -exec chmod <permissions for files> {}\; (644?)

should help, though executable files will have to be fixed later

---

### Post by gallifrey on 2010-08-14
Many thanks. These are all icons, so I don't think I need to worry about the executable bit. So long as they can be read/accessed by users other than root after installation.

---

