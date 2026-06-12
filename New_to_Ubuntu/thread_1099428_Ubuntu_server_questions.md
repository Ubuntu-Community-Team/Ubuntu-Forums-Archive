---
title: "Ubuntu server questions"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by mangurt on 2009-03-18
Greetings all,
I recently installed ubuntu server 8.10 on an old computer, but I have 2 questions.  I have 2 external hard drives that have a lot of information.  Both drives are formatted NFTS.  I would like to have access to my home network so my family can look at the pictures and movies that are stored on both drives.
Here are my questions:
1)  Using webmin, I can see both drives when I look at partitions on local drives, but I cannot find the drives when I go to Samba Windows file sharing (I have one window computer).  I looked in the /media folder and /mnt but there's nothing showing up.  How would I go about finding out where these drives are mounted.
2)  These drives used to be connected to an Ubuntu box, so I'm pretty sure the permissions is set up for that box.  Is there any way of changing the permissions in the server to be able to read and write with the server?
Thanks

---

### Post by marshall.robert on 2009-03-18
1) You have to manually mount your drives.
2) I don't quite understand you.

---

### Post by mangurt on 2009-03-18
Ok, manually mounting the drives should be no problem

As for question #2:  The external hard drives were attached to my desktop before I got this server set up, so, the permissions on all the folders are for "ed" to read and right.  I would like to set it up so the server would have access to read and write to the drives.

---

### Post by mangurt on 2009-03-19
Ok, I have the hard drives mounted!  Yeah, now the only problem is when I try to set up a folder for my daughter to use, I get an error stating I don't have permissions to create the folder.  I am trying to create the folder on the external hard drive.

---

### Post by sahabcse on 2009-03-19
Hi

Mounting the NTFS parttion follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by mangurt on 2009-03-19
Outstanding!!!  That really worked.  I have both external hard drives mounted, and I can read and write to them!!!

Now the only problem I see is that the transfer is rather slow (about 1 mbit a second).  I don't know if that's because I am trying to transfer something wirelessly or not (wireless laptop to server client).  I would think that it would be faster than that though.  Any ideas?

---

