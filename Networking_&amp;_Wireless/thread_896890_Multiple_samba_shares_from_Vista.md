---
title: "Multiple samba shares from Vista"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Mailme on 2008-08-21
My system;

Terminal 8.04.1 with a 40gb as my boot drive & a 250gb set up in fstab as follows - 

/dev/sdb1       /home/videolan/video     ext2    defaults,errors=remount-ro 0       1
/dev/sdb2       /home/music/mp3     ext2    defaults,errors=remount-ro 0       1
/dev/sdb3       /home/photo/pictures     ext2    defaults,errors=remount-ro 0       1

My problem;
I'm trying to set up 3 map network drives from within Vista to each of the Ubuntu folders above, i.e. one share for each folder. The first is successful but then when I try to map the second Vista complains with the following;

"The network folder specified is currently mapped using a different user name and password.
To connect using a diferent user name and password, first disconnect any existing mappings to this network drive."

Is it not possible to have Vista access multiply user folders on the same Ubuntu PC? And if not, what is the correct way to setup maps for these 3 folders.

Many thanks to anyone who responds.
Mailme

---

### Post by Iowan on 2008-08-21
Does it matter which folder is mapped first?  More specifically, do the folders (drives) all have the same permissions/owners?

---

### Post by Mailme on 2008-08-21
No, each folder is owned by a diferent user. I've tried setting up multiple folders with the same user and still I can only access the first mapped drive. After that I get the same Vista error message.

---

### Post by Iowan on 2008-08-21
I suppose I should back up a minute and read what you sent... Just as I was including [this]("http://ubuntuforums.org/showthread.php?t=288534") thread, I noticed you're mounting the drives as ext2. Check the **man mount** page for the **user(s)** option(s).

---

