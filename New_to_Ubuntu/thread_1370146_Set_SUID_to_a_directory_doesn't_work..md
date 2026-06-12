---
title: "Set SUID to a directory doesn't work."
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Najand on 2010-01-01
I don't know why it goes wrong. 
I did gave 777 permission to a directory.
```
user1@host:~$ mkdir public
user1@host:~$ chmod 777 public
```
Then I added SUID bit to the directory permission.
```
user1@host:~$ chmod u+s public
```
Then I checked permissions using ls command.
```
user1@host:~$ ls -ld public
drwsrwxrwx 2 user1 group1 4096 2010-01-02 12:42 public/
```
So the SUID has been set.
The I tried to create a file in the directory using user2.
```
user1@host:~$ su user2
password:
user2@host:~$ cd /home/user1/public
user2@host:/home/user1/public$ touch file
user2@host:/home/user1/public$ ls -l
total 0
-rw-r--r-- 1 user2 group2 0 2010-01-02 12:51 file
```

Shouldn't the ownership of all files created in a directory with SUID changes to the owner of the directory? Is it a bug or should it be like this? Thanks for your help in advance.
PS. I don't want to change "umask" value.

---

### Post by mkoehler on 2010-01-01
Seems like a bug to me.

---

### Post by Najand on 2010-01-01
Seems SUID is not defined for directories in Linux. I have to use SGID instead.

---

### Post by bodhi.zazen on 2010-01-01
> **Najand said:**
> Shouldn't the ownership of all files created in a directory with SUID changes to the owner of the directory? Is it a bug or should it be like this? Thanks for your help in advance.
PS. I don't want to change "umask" value.

No, that is not how sticky bits work.

See :

[http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php](http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php)

---

### Post by jbrown96 on 2010-01-01
This is not a recommended way to grant access to other users. You should create a group that user1 and user2 belong to, them make public owned by that group.

1) Undo the insecure permissions. ```
sudo chmod 660 public
```

2) Create a group to which both users belong. ```
sudo groupadd shared
``` you can change "shared" to anything you want. 

3) Add all users that need access to the shared group. ```
sudo usermod -aG shared user1
``` repeat for all users

4) you will need to logout before the new group memberships take effect.

SUID is not recommended; there are just a handful of programs that need them.

---

### Post by Najand on 2010-01-01
> **bodhi.zazen said:**
> No, that is not how sticky bits work.

See :

[http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php](http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php)

Thanks for the reply. In fact it works for SGID./
But I had this imagination from old days on UNIX that it works for SUID too. However it seems it is not working for linux. 

I used this reference anyway: 
[http://tldp.org/LDP/intro-linux/html/intro-linux.html#sect_03_04_02_05](http://tldp.org/LDP/intro-linux/html/intro-linux.html#sect_03_04_02_05)

---

### Post by Najand on 2010-01-02
> **jbrown96 said:**
> This is not a recommended way to grant access to other users. You should create a group that user1 and user2 belong to, them make public owned by that group....

Well, in my case I want to have two separate groups for both users. It seems it works now with SGID bit set.

---

