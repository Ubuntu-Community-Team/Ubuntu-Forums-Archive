---
title: "2cd Internal Hardrive no Privileges"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by utfan2012 on 2009-12-27
I have searched for the answer, but i don't really understand what i am coming across. Will some one explain to me  When i copy files from my 160Gb hd to my 1tb newly installed hd I don't have all the permission that i should.Also only root can create  or delete on the 1Tb drive. Thanks.

---

### Post by Elfy on 2009-12-27
Try opening nautilus as root

```
gksudo nautilus
```

Open the new drive - right click - Proprties - Permissions and change them to suit you.

Generally I though make folders to mount in fstab and chmod and chown them in a terminal, similar to this [http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5) though that was specific to someone elses partitions.

---

