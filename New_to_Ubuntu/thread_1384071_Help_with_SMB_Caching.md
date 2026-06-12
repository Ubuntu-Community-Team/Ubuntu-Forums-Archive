---
title: "Help with SMB Caching??"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Image0fman on 2010-01-18
I use samba on one of my linux boxes that acts like a server. Whenever I (unshare) something, it still appears when other computers access the share on my linux box. The unshared folder is obviously unaccessible but it pisses me off that it still shows up on other machines. Is this some type of samba cache? Can it be resolved? Thanks in advance

---

### Post by cariboo on 2010-01-18
How are you "unsharing" the directory?

---

### Post by Image0fman on 2010-01-18
right clicking and unchecking the share option

---

### Post by argosreality on 2010-01-18
Yes, there is a cache for samba. As to how to fix it, I've got no clue. Found plenty on google looking for it but I doubt you want to reload the samba.conf each time you delete a file ;)

---

### Post by Image0fman on 2010-01-20
Fixed this issue by editing the smb.conf file. For some strange reason the two directories that I wasn't sharing anymore were all the way at the end of the smb.conf file. All I did was simply delete them and now you can only see what I am currently sharing.

---

