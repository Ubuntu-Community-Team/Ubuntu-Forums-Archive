---
title: "Incorrect Permissions for FTP user's home directory. . ."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-09-06
Hi!  I have enabled anonymous uploads for my vsftpd powered FTP server.  Not to worry, as it is behind a firewall.  However, I think the permissions are wrong for the ftp user's directory, as I get a "Permission denied" error.  What are the correct permissions for /home/ftp?

Thanks in Advance!

---

### Post by k33bz on 2009-09-06
> **pi.boy.travis said:**
> Hi!  I have enabled anonymous uploads for my vsftpd powered FTP server.  Not to worry, as it is behind a firewall.  However, I think the permissions are wrong for the ftp user's directory, as I get a "Permission denied" error.  What are the correct permissions for /home/ftp?

Thanks in Advance!

Hi, are you wanting permissions from just your self or for anyone, or just a  group of people?

---

### Post by pi.boy.travis on 2009-09-06
Thanks for the reply!

Yes, anyone should have access to the ftp directory.  This server is for my computer behind my firewall to share files.  I was using samba, but I figured FTP would be faster and better suit my Linux clients.

---

### Post by k33bz on 2009-09-06
> **pi.boy.travis said:**
> Thanks for the reply!

Yes, anyone should have access to the ftp directory.  This server is for my computer behind my firewall to share files.  I was using samba, but I figured FTP would be faster and better suit my Linux clients.

if you want everyone to have full access to that file do this
in the cli```
chmod 777 /home/ftp 
```

---

### Post by pi.boy.travis on 2009-09-06
> **k33bz said:**
> if you want everyone to have full access to that file do this
in the cli```
chmod 777 /home/ftp 
```


WOW. . . that was easy. . .

Thanks!

---

### Post by pi.boy.travis on 2009-09-06
OK, now I am having some issues:

If I access the server using firefox, I get: ERROR500, child died

If I use nautilus, I get: Could not open anonymous@192.168.1.150, nautilus can't handle 'ftp' locations.  Same thing if I use the 'Connect to server' dialog

If I use gFTP, I can upload files and create directories, but I can't delete anything.  Is there a way to allow my clients to delete files?

---

### Post by k33bz on 2009-09-06
using chmod 777 would allow complete access to the file or directory, read, edit, even execute, for everyone. I am not sure why you are not able to delete them.

Have you tried using it through your actual IP address and not your local IP apdress?

---

### Post by pi.boy.travis on 2009-09-06
OK, I did some research, and it turns out that vsftpd gets upset if you change the ftp user's home directory's permissions.  So, I tried it with a folder I made inside /home/ftp and it worked, but I still can't delete files.  I think that perhaps this is by design, you wouldn't want someone else to be able to delete your files, would you?

---

