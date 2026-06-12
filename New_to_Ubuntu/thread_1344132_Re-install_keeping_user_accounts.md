---
title: "Re-install keeping user accounts"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-12-02
What is the best way to re-install Ubuntu keeping my current user accounts. I have a separate /home partition and would like to keep the user accounts and data already there (6 accounts).

Is there an easy way to do this?

---

### Post by jbrown96 on 2009-12-02
You will need to copy /etc/passwd, /etc/group, and /etc/group- to your new installation. There may be others as well, but I think that should cover most of it. It would be a good idea to backup /etc/ before you reinstall, in case you need some other files. /etc/ is small; mine is only 14MB.

---

### Post by marco123 on 2009-12-02
Re-install, choose Specify partitions manually when you get to the partitioning screen, choose to format / but not /home

---

### Post by jbrown96 on 2009-12-02
> **marco123 said:**
> Re-install, choose Specify partitions manually when you get to the partitioning screen, choose to format / but not /home

This will preserve the data, but not the users. User names are not important; it's the user id that matters. Ubuntu always starts with the same uid (1000 i think) and increments for each new user. The problem with marco123's method is that you will have to create the users in the exact same order, and there is still a possibility that things could go wrong. 

You are much better off to copy the files I said. Otherwise, you will need to use adduser and addgroup to replace all your users and groups. Information can be found with ```
man adduser
``` ```
man addgroup
```

---

### Post by celticbhoy on 2009-12-02
> **jbrown96 said:**
> This will preserve the data, but not the users. User names are not important; it's the user id that matters. Ubuntu always starts with the same uid (1000 i think) and increments for each new user. The problem with marco123's method is that you will have to create the users in the exact same order, and there is still a possibility that things could go wrong. 

You are much better off to copy the files I said. Otherwise, you will need to use adduser and addgroup to replace all your users and groups. Information can be found with ```
man adduser
``` ```
man addgroup
```

How do I deal with ubiquity asking for user details on install?

---

### Post by jbrown96 on 2009-12-02
The issue here is that whatever user you enter into the installer gets user id 1000. You need to make sure this matches up from your old install. It's not terribly important, but it will save you a little trouble. 
There's two ways to find this.
#1 Remember which user you set up first in your old install.
#2 check /etc/passwd ```
cat /etc/passwd | grep .*1000.*
``` that find the user with id 1000. That's the user you need to setup in the installer.

When you are doing the disk partitioning, you need to choose your /home parition, then click edit. Choose the file system type and mount point. MAKE SURE THAT THE FORMAT BOX IS NOT CHECKED! Proceed with the installation, and create the proper user.


You may be inclined to create a "dummy" user during installation, thinking that you can just delete it later. However, you will run into issues with the user IDs as well.


Edit: Disregard everything I just said. It doesn't particularly matter what you do during installation. When you copy over those three files I mentioned earlier, it will override anything you did during the installation.

---

