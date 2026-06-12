---
title: "How to deny file/partition access to other users."
date: 2009-03-18
forum: New to Ubuntu
---

### Post by suitedaces on 2009-03-18
I want to make my /media/disk (vista partition) invisible to all users except my own (imaginatively named) "ubuntu" user account, due to the nature of some of the files on there, ahem. Anyway, even when I go into a guest session (just to test it out), I can easily access the entire partition as it is on the desktop already mounted. Is there any way to deny access to this for both the guest, and another user (tracey) that doesn't require me to give out my password to them for other tasks?

---

### Post by iaculallad on 2009-03-18
You can't set Linux permissions and ownership to a NTFS formatted partition/drive. Setting the umask would probably be the solution.

---

### Post by bumanie on 2009-03-19
You may like to look at [truecrypt]("http://www.truecrypt.org/") - it can encrypt separate files, whole partitions and entire hard drives.

---

### Post by Jeff250 on 2009-03-19
Try this:
In System -> Administration -> Users & Groups:
Create a group called ntfs.  Then edit the group to add all of the users that you want to be able to access the ntfs partition.

Next, run:
```
sudo chgrp ntfs /media/disk
sudo chmod 770 /media/disk
```

The first command will change your ntfs partition's group owner to your new group.  The second command will change the permissions so that only root and everyone in the ntfs group will be able to access the partition.

---

### Post by suitedaces on 2009-03-19
Thanks. Before I run the command, does that 770 have to match the group ID?

---

### Post by Jeff250 on 2009-03-19
No, the breakdown of 770 is as follows:
7: give all permissions to the user owner
7: give all permissions to the group owner
0: give no permissions to anyone else

Type:
man chmod
or google for chmod octal permissions for more information on how this all works.

---

