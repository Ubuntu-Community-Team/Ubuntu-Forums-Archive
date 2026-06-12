---
title: "Mount FTP folders"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by Mr K on 2008-06-07
Hi!
I have decided to open a new because in a month of googoling i haven't found an answer to my problem! I have Nas disk connected on my home network, and i want to access it and mount it has a folder in my home directory. The problem is that i cannot manage permission or modify files once they are on the nas. Using filezilla or gftp i don't find these problems but using curlftps to mount the disk has a directory i encounter problems on managing the folders/files permissions.
The command i use (mainly) is
```
curlftpfs -o umask=0777,uid=1000,gid=1000  ftp://admin:pass@192.168.0.101 /home/roby/Share/

```
I have tried modifying it a bit but the problem doesn't go away. :(
Can someone tell me what I'm doing wrong?

---

### Post by Mr K on 2008-06-08
Somebody? Pleeeeeeeease!

---

### Post by rshel on 2008-06-16
Have you tried samba and cifs? I have a simpleshare NAS which is also a print server. My problem was that I had not configured the NAS to require a userID and password. In addition to being security foolish, this turned out to be the stumbling block to getting my NAS to mount automatically with the correct permissions.  So, I configured it to require an ID and password.  Then I changed my fstab to look like this (with a similar line for each folder or share on the NAS):  what my fstab looks like:

//simpleshare/sharename1 /mnt/Folder1 cifs credentials=/home/userfolder/.passwordfilename,uid=username,gid=username 0 0

//simpleshare/sharename2 /mnt/Folder2 cifs credentials=/home/userfolder/.passwordfilename,uid=username,gid=username 0 0


Hope this helps you.

curlftpfs is not necessary for a NAS, as far as I know.  And I've never gotten it to auto-mount an ftp site.

---

### Post by Mr K on 2008-07-20
Thanks it helped :)

---

