---
title: "Basic concept of umask ?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by honey_bee on 2010-04-14
H,
     Iam new in Linux. There are some few questions in my mind  related to umask. I want to know that is the default file and directory  permissions ?

2- When we use umask (022) command in terminal. and create a new file  then the permissions applied for new file is for that sesscion  and when  the system will reboot linux will take automatically its default  permission from etc/bashrc or /etc/profile ?

3- Can we make our own umask or the professional way is to follow 022  only ?

4- What is the benefit of umask in Linux?

thanks in advance
honey

---

### Post by Brandon Williams on 2010-04-14
The umask is referred to as "the file mode create mask". It applies only to the permissions of newly created files. A new file being created will have the permissions indicated by the umask turned off. If you access the file later (including after a reboot), the umask will never have an impact on it, because the file already exists. Likewise, if you change the umask, it will have no impact on existing files, only on new files being created.

You can set any umask you desire, but you must be careful to ensure that your umask does not limit your ability to access files that you create yourself. Generally, you should only change the final to digits of the octal number. In practice, the two most common umask values are 022 (which means that other groups and users allowed to read and execute your files by default) and 077 (which means that other groups and user are not allowed any level of access to your files by default). I use the later setting (077) because I work on a lot of different public systems, and on some of them, it is very important that no one else be able to see the files I create unless I explicitly modify the permissions on the file.

The benefit of umask, as indicated above, is that it allows you to decide what level of access others should be allowed to have to files you create. It doesn't prevent you from using different priveleges for specific files; it just helps to ensure that you follow a specific security policy by default.

---

