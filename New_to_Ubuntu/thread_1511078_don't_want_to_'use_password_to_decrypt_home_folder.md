---
title: "don't want to 'use password to decrypt home folder'"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by 4chan on 2010-06-16
a good friend of mine asking this to me :

' some days ago i reinstalled ubuntu and choose 'use password for decrypt home folder' now when i try to reinstall it again with 'specify partitions manually' i cannot choose 'automatically log in' or 'require password to log in'. how to fix it? '

can you please help me to answer this question.

regards.


Allison

---

### Post by -kg- on 2010-06-16
What it sounds like is that your friend is trying to reinstall while preserving his /home partition and his /home partition is encrypted.  Likely, this would not allow the login option, since his /home partition is encrypted and requires a password to access it, and root must have access to it in order to fully boot.

The only thing I can think of is that he must un-encrypt his /home partition and then reinstall Ubuntu.  How to do this, I don't know...I've never found it necessary to encrypt my /home partition.

Though the article addresses a different issue, you may find what you need from the following page:

[Removing Encryption from Home Directories in Ubuntu 9.10 & 10.04]("http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/")

The way I read this article, the Ubuntu Live CD would work for this.

---

### Post by mbzn on 2010-06-16
Probably the easiest would be to backup his /home to a non encrypted storage and format, create a new /home partition and just copy it back.

---

### Post by 4chan on 2010-06-16
**-kg-** & **mbzn** thanks for your help. after reading your replies i think he needs to fully backup data from home folder and then create new home partition.

i will mark this thread as solved.

---

