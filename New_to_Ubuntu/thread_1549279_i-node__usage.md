---
title: "i-node  usage"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by jharp5 on 2010-08-09
I  was  briefly  introduced  to  i-nodes  today  in  class  today.  I  was  wondering  if  an  i-node  could  be  used  to  locate  a  file  in  the  ubuntu  file system.:KS

---

### Post by Brandon Williams on 2010-08-10
[Here](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html) is an explanation of inodes with a listing of what is (and isn't) contained in the inode. It's part of a series of articles about *nix filesystems.

Among other things, this article shows that there is no information in the inode about the name of the file or where the file is located within the filesystem. This lack of location/name information allows that inode to have multiple names and to be located in multiple places within the filesystem.

You can use the inode number as a key for the find utility, which allows to locate all references to that inode number within the filesystem.

---

### Post by jharp5 on 2010-08-11
thanks  for  the  information.  It  was  and  is  highly  benefical.  Thank  you  for  being  one  the  lights  to  my  learning  LINUX programming.

---

### Post by LightningCrash on 2010-08-11
> **jharp5 said:**
> I  was  briefly  introduced  to  i-nodes  today  in  class  today.  I  was  wondering  if  an  i-node  could  be  used  to  locate  a  file  in  the  ubuntu  file system.:KS

find / -inum 5984


where 5984 is the inode number.

---

