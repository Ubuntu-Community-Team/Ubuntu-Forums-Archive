---
title: "Problems with samba shares in fstab"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by oliver369 on 2006-11-10
I have got a big problem whilst mounting my samba shares which is driving me insane.
The share is put like so in the fstab
**//Mercury/D /mounts/MercuryD smbfs dmask=777,umask=777   0 0**

I want this share to accessible to all users on the machine with read and write permissions. The mount doesnt mount on startup but when I go to the terminal and type **sudo mount -a** it then asks me for my password twice and then succesfully mounts the share. If I add another share to the fstab :
**//Mercury/D /mounts/MercuryD smbfs dmask=777,umask=777   0 0**
The same happens it doesnt not mount upon startup and when type **sudo mount -a** in the terminal it asks me 3 times for my password.

I presume that this problem is related to user permissions...
I would really appreciate a helping hand on this needless to say I have looked on google and other forums and I cannot find anything...:confused:

---

### Post by oliver369 on 2006-11-10
I managed to get the shares working with cifs instead of smbfs but now all users except root cannot see the contents of the mounted folder...

---

### Post by Iowan on 2006-11-10
I suspect you've already seen it... otherwise, 3rd link in my sig might be helpful.

---

