---
title: "How do I share music and photos with other users?"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by mrwaistcoat on 2010-09-23
All the music and photos on our family PC are under my user name.

I've tried all the file sharing options, but none of the other users can access my files.

Is the file sharing options for sharing across a network ?  I don't have a network, I just want all users of the same PC to be able to easily access my media directories

Is there a way to do this ?

Many thanks

---

### Post by frup on 2010-09-23
So you have files in one /home/user/dir/ that you want to share with /home/user2/?

You're going to want to learn about how users and groups and permissions work on Ubuntu. There are a few ways you will be able to achieve the desired effect, with varying degrees of security.

What I would do is create a group called "share" for example. I would make the users who are allowed to share in those folders members of that group and then apply the permissions to the main share directory so that members of the group share have read/write access (perhaps only read if you want the master user to have control)

---

### Post by bailbath on 2010-09-23
> **mrwaistcoat said:**
> All the music and photos on our family PC are under my user name.

I've tried all the file sharing options, but none of the other users can access my files.

Is the file sharing options for sharing across a network ?  I don't have a network, I just want all users of the same PC to be able to easily access my media directories

Is there a way to do this ?

Many thanks
Can you tell us what operating systems you want to share files with.
Ian

---

### Post by migs73 on 2010-09-23
> **bailbath said:**
> Can you tell us what operating systems you want to share files with.
Ian

I would assume as they are using the one PC and the files are under his **user name** they are all using Ubuntu?

---

### Post by mastablasta on 2010-09-23
> **bailbath said:**
> Can you tell us what operating systems you want to share files with.
Ian
 
 
He is trying to share on same computer.
 
> What I would do is create a group called "share" for example. I would make the users who are allowed to share in those folders members of that group and then apply the permissions to the main share directory so that members of the group share have read/write access (perhaps only read if you want the master user to have control) 
 
What is public folder for then?
 
also i think you should be abel to access the files at least to just read them. afterall these are nonessential files (for the system)

---

### Post by nothingspecial on 2010-09-23
Set the permissions to 644

That way everybody will be able to view the photos but they won`t be able to delete them by mistake. Only you are free to add to or delete the folder and it`s contents.

```
sudo chmod -R 644 /path/to/folder
```

---

### Post by azertyh on 2010-09-23
hi
to share a folder, type these commands in a terminal :
```
john@ordinateur:~$ sudo -s
[sudo] password for john:
root@ordinateur:~# addgroup partageurs
root@ordinateur:~# adduser john partageurs
root@ordinateur:~# adduser mary partageurs
 
root@ordinateur:~# echo "umask 0002" >> /etc/profile
 
root@ordinateur:~# mkdir /home/Partage
root@ordinateur:~# chgrp -R partageurs /home/Partage
root@ordinateur:~# chmod -R g+rwx,o-rwx /home/Partage
root@ordinateur:~# chmod -R g+s /home/Partage
root@ordinateur:~# exit
exit
```
 
in this case, the folder /home/Partage is sharing between john and mary. john and mary can create, modify, copy and delete files in this folder.
to add another user, type just the third command with user right name.
i found this tuto on the french forum, i can put the link if you want.

---

