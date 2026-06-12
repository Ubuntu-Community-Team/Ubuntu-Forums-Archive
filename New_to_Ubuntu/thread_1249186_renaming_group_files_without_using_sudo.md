---
title: "renaming group files without using sudo"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by cmroanirgo on 2009-08-25
Hi,

It appears that I don't understand what's going on with file permissions.
I have a normal installation of ubuntu 9.04 and have installed apache2 with all the default stuff.
I have a file in /var/www/subdir/file.zip that has the following permissions:
> -rwxrwxr-- 1 www-data www-data 18432 2009-08-25 07:07 file.zip

If I am logged in (using putty) using the username I provided during setup I find that I can't rename the file:
> mv: cannot move 'file.zip' to 'ile.zip': Permission denied

Note that I am a member of the www-data group:
> groups MyNameHere
MyNameHere adm dialout cdrom www-data plugdev sambashare lpadmin admin. (I used sudo adduser MyNameHere www-data)

Why can't I rename this file?

The real problem is that I want to be able to SFTP to /var/www and upload files, but I can't actually change anything, although I can read and browse just fine.

---

### Post by Ocxic on 2009-08-25
the file must also belong to that group?

---

### Post by mcduck on 2009-08-25
Check the ownership & permissions of the /var/www/subdir.

---

### Post by prshah on 2009-08-25
> **cmroanirgo said:**
> 
I have a file in /var/www/subdir/file.zip that has the following permissions:
but I can't actually change anything, although I can read and browse just fine.

You need to check the _directory_ permissions, ownership and group. Your username / group must be either the owner / group of /var/www, and /var/www must have write access enabled for the particular user/group. DO NOT ENABLE WRITE ACCESS FOR EVERYBODY on /var/www.. that's a sure way for vandals to mess with your website.

Post back if you need more clarifications.

---

### Post by cmroanirgo on 2009-08-25
> **prshah said:**
> You need to check the _directory_ permissions, ownership and group.

Thanks for that. Actually, that makes some sense, since file renaming is actually a directory thing rather than modifying the file itself.

Since I need to enable write access for myself (when using putty or sftp) I presume I'll need to add group access for myself for every folder and file from /var/www downwards.

Would calling > cd /var/www
sudo chmod -R g+w . be the right choice? Will it be reducing my security (provided there is only myself and www-data user that is part of the www-data group)?

---

### Post by prshah on 2009-08-26
> **cmroanirgo said:**
> 
Since I need to enable write access for myself (when using putty or sftp) I presume I'll need to add group access for myself for every folder and file from /var/www downwards.

Your code seems reasonable, but I cannot comment on the security aspect of it (not enough knowledge).

On the face of it, it seems fine. However, on my server, /var/www is owned/grouped root, and only u(ser) has write access (u+w).

So if you plan to allow users of the group www-data to have write access, you will also need the switch group ownership of /var/www to www-data. I don't know if this can be done or not. (Eg, in the case of wine, it will refuse to start with the users credentials unless the ~/.wine is owned by the user.).

---

