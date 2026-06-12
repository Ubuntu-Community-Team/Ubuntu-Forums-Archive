---
title: "Swat Help Links are broken"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by sephirothsigep on 2008-02-01
alright i have swat and samba both working. i used this guide[https://help.ubuntu.com/community/Swat]("https://help.ubuntu.com/community/Swat") for getting swat working with one change. inorder for swat to make changes to the smb.conf file i had to change the permission of the smb.conf file so that all users had read write. then all worked as planned. then to secure samba i changed the permissions of the file back. 


alright now to my problem. all of the help links next to the fields are not working. when i click on one of them i get a 404 error(FILE NOT FOUND). what i wanted to know is what i can do about this to fix this problem?

i attached a picture of what i have going on let me know if you can do anything for me.

---

### Post by jetsam on 2008-02-01
I think you need the samba-doc package.  Try
```
sudo apt-get install samba-doc
```
and see if that fixes it.

---

### Post by sephirothsigep on 2008-02-01
> **jetsam said:**
> I think you need the samba-doc package.  Try
```
sudo apt-get install samba-doc
```
and see if that fixes it.

YEP what would you know that fixed it. thanks such any easy fix too.

---

