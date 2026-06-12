---
title: "VSFTPD Restrict"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by subhadeepgayen on 2011-09-06
Hi,

I want to restrict ftp users from traversing to their higher directories, i know there is a option to chroot the user to his home directory, but in that case, if there is any folder inside his home directory he cannot open it, so i can i achience that?

Thanks,
S>G

---

### Post by Bodsda on 2011-09-06
> **subhadeepgayen said:**
> Hi,
 
I want to restrict ftp users from traversing to their higher directories, i know there is a option to chroot the user to his home directory, but in that case, if there is any folder inside his home directory he cannot open it, so i can i achience that?
 
Thanks,
S>G
 
They would only be able to access directories that they have permissions on. 
 
Can you elaborate a bit more on the scenario? Who is connecting, connecting to what, trying to acces what, current permissions
 
The way I think you are describing is that they access /home/theirusername, and can also access /home. If this is the case I dont think they shoulld be able to traverse to /home and then access /home/someoneelse. Is that not secure enough?
 
Bodsda

---

### Post by subhadeepgayen on 2011-09-06
ok let me explain the situation,

i have a folder /home/subhadeepgayen/downloads

it is shared between several users by creating a group and chown it and the folder is set as home for all users.  folder is also made 755 so they can access it.

now problem is everybody has their own username password with which they can login to ftp, when they login, they can go all way back to root where they can access other files, they may not be able to copy it but they are able to check it, like etc/www/ folders and etc, i want to make such that they cannot traverse to higher directory at all, so i tried using chroot , but though that works, now the users cannot traverse into the folders inside the download directory.

This is my problem. i want both to work.

Thanks,
S>G

> **Bodsda said:**
> They would only be able to access directories that they have permissions on. 
 
Can you elaborate a bit more on the scenario? Who is connecting, connecting to what, trying to acces what, current permissions
 
The way I think you are describing is that they access /home/theirusername, and can also access /home. If this is the case I dont think they shoulld be able to traverse to /home and then access /home/someoneelse. Is that not secure enough?
 
Bodsda

---

### Post by Bodsda on 2011-09-06
> **subhadeepgayen said:**
> ok let me explain the situation,
 
i have a folder /home/subhadeepgayen/downloads
 
it is shared between several users by creating a group and chown it and the folder is set as home for all users. folder is also made 755 so they can access it.
 
now problem is everybody has their own username password with which they can login to ftp, when they login, they can go all way back to root where they can access other files, they may not be able to copy it but they are able to check it, like etc/www/ folders and etc, i want to make such that they cannot traverse to higher directory at all, so i tried using chroot , but though that works, now the users cannot traverse into the folders inside the download directory.
 
This is my problem. i want both to work.
 
Thanks,
S>G
 
Where did you chroot them to? If you set the chroot to /home/subhadeepgayen/downloads   then they should be able to access everything below that directory
 
Bodsda

---

### Post by subhadeepgayen on 2011-09-06
i did chroot_local_user=YES in config file of vsftpd, and it locks user in that directory but also does'nt allow him to acces any child directories :(

> **Bodsda said:**
> Where did you chroot them to? If you set the chroot to /home/subhadeepgayen/downloads   then they should be able to access everything below that directory
 
Bodsda

---

