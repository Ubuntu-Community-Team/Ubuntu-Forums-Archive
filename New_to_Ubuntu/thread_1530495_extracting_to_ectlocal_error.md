---
title: "extracting to /ect/local error"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by paul88 on 2010-07-13
I am trying to extract some tar.gz files to /ect/local but I do not have permission to do so. Sudo doesn't work. Is there a reason why and can I get around it?

---

### Post by mbzn on 2010-07-13
It might be because /etc/local doesn't exist, 
try
```
sudo mkdir /etc/local
```
and then repeat (with sudo)

---

### Post by paul88 on 2010-07-13
I have the dirctory

```
paul@paul-laptop:/usr/local$ ls
bin  etc  games  include  lib  man  sbin  share  src
paul@paul-laptop:/usr/local$
```I am trying to do this

```
paul@paul-laptop:/usr/local$ gunzip < /media/cdrom/MySQL/binary/Linux/mysql-5.0.51a-linux-i686.tar.gz | tar xf -
```This is some of the output i am getting

```
tar: mysql-5.0.51a-linux-i686/include/my_alloc.h: Cannot open: No such file or directory
tar: mysql-5.0.51a-linux-i686/include/my_time.h: Cannot open: No such file or directory
tar: mysql-5.0.51a-linux-i686/include/m_string.h: Cannot open: No such file or directory
tar: mysql-5.0.51a-linux-i686/include/my_tree.h: Cannot open: No such file or directory
tar: mysql-5.0.51a-linux-i686/include/my_user.h: Cannot open: No such file or directory
tar: mysql-5.0.51a-linux-i686/COPYING: Cannot open: No such file or directory
tar: Exiting with failure status due to previous errors
```

---

### Post by Sanjeevtrip on 2010-07-14
Check your tar file it its correct
tar -tvzf tar.gz

if its ok then you can do
tar -xvzf tar.gz -C /etc/local

---

