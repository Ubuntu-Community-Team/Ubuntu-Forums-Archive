---
title: "Help setting up samba."
date: 2009-01-01
forum: New to Ubuntu
---

### Post by halfelite on 2009-01-01
I have made a samba share that works with the main account under ubuntu with both read and write access. I want another user to be able to access the same share but with only read access. I think its something to do with the folder permissions itself. I created another user named read with no ssh access and it cant access the share.

Here is my config i have
# stuff Share.
[STUFF]
  comment = Stuff
  read only = yes
  path = /mnt/Stuff/Stuff
  guest ok = yes
  write list = chris

this is the permissions i have on the folder right now.
drwxrw-rw- 8 chris 1005  4096 2008-12-30 02:02 Stuff

and the directories in that folder are

drwxr-xr-x    3 chris chris   4096 2008-12-30 02:02 Apps
drwxr-xr-x    9 chris chris   4096 2008-12-17 22:59 Docs
drwxrw-rw-  326 chris chris  28672 2008-12-29 21:38 Docs2

---

### Post by Delever on 2009-01-01
No need to get into config files so fast, first make sure you enabled privileges to share files for that user in user administration dialog. System -> Administration -> Users and Groups.

EDIT: you can skip my post, it seems I am lacking knowledge here, sorry

EDIT2: switched to ubuntu when I noticed that there is GUI for file sharing...

---

### Post by halfelite on 2009-01-01
> **Delever said:**
> No need to get into config files so fast, first make sure you enabled privileges to share files for that user in user administration dialog. System -> Administration -> Users and Groups.

EDIT: you can skip my post, it seems I am lacking knowledge here, sorry

EDIT2: switched to ubuntu when I noticed that there is GUI for file sharing...


Not a problem. I dont have a gui installed. i think when you add users to the share its changing the permissions of the folder as a group im not positive though so waiting for confirmation.

---

### Post by halfelite on 2009-01-01
Ok after testing more i cant get user share to access the mount folder from ssh either. I changed permissions on the folder to owner chris group chris. and

chmod -R 774 wich should have let the user share use it. still didnt work then tried
chmod -R 766 and still nothing.

---

### Post by halfelite on 2009-01-01
Ok did more testing.

I remade user share and using -G added him to both groups chris and sambashare. but still no luck does not access the share point nor can the user reach it via ssh.

I dont understand why setting 755 should give everyone access to the dir a least.

---

### Post by Delever on 2009-01-01
Shouldn't users own their shared folders (by default)?

---

### Post by cariboo on 2009-01-01
I would suggest setting the ownership of the share on the server back to root and set the permissions to world read/writeable. To do this on the server type:

```
sudo chmod -R 777 sharename
```

where sharename is the directory you want to shre. then on your desktop computers whether they ar Window or Linux you don't have to fool around with ownership and permissions.

Once you have things working, then you can experiment with permissions.

Jim

---

### Post by halfelite on 2009-01-02
> **cariboo907 said:**
> I would suggest setting the ownership of the share on the server back to root and set the permissions to world read/writeable. To do this on the server type:

```
sudo chmod -R 777 sharename
```

where sharename is the directory you want to shre. then on your desktop computers whether they ar Window or Linux you don't have to fool around with ownership and permissions.

Once you have things working, then you can experiment with permissions.

Jim

Thanks that works but why wont it work if others is set to read

Should anyone that is not the owner or group then be able to read the dir?

---

### Post by handydan918 on 2009-01-02
> **halfelite said:**
> Thanks that works but why wont it work if others is set to read

Should anyone that is not the owner or group then be able to read the dir?

If the file in question is owned by root, then you can either have access to it via sudo, or add yourself to group that has rw permissions. 
See man chgrp for details on how to do this. 
Once you have changed the group to include yourself, you can restrict the rights of "others" with chmod. 
Let's assume a file called eeeeeeeeeeeebuntu!
ls-l shows us 
```
-rw-r--r-- 1 root daniel 209984 2008-12-26 10:25 eeeeeeeeeeeebuntu!
```

The owner is root, the group is daniel, and we are  going to give daniel write permissions while leaving everyone else at read-only, like so:

```
chmod 764 eeeeeeeeeeeebuntu!
```
yielding a new ls -l output of 

```
-rwxrw-r-- 1 root daniel 209984 2008-12-26 10:25 eeeeeeeeeeeebuntu!
```

HTH!

---

