---
title: "file/folder permssion"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by pkd78 on 2009-01-31
Hi all,

I'm running ubuntu server 8.10 and need to know how to give a normal user(ex.test1) read access to folder/file. The folder/file owner is root. I only need to give read access to test1 user.

thanks in advance

---

### Post by utnubuuser on 2009-01-31
sudo chmod -r 744 /path/to/and/name/of/folder

-r = recursive, meaning all the same permissions apply to any files within the folder
7 owner =all permissions
4 group =access only
4 others=access only

---

