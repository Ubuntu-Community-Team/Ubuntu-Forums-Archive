---
title: "john-the-ripper password file"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-30
The file that I am tryig to crack that contains my password, has been unshadowed. However, when I look at it by gediting it the files has many lines. I thought thsat such a file would simply have the hashed password, and nothing else - one line total. This file has over 70 lines. I think that something is wrong, but maybe not. I unsdaowed and combined two files into this one file, but it seems to have far too many lines in it.
 
Is is supposed to be that way or did I do something wrong? I am using Ubuntu 10.04.
 
 
Newport_j

---

### Post by oscar_alfonso on 2010-10-24
Your file contains all system accounts, not just user accounts.  You might have accounts such as ntp or FTP.  You can cut them out or specify which accounts to crack.

---

