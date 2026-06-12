---
title: "Ubuntu - General Input/output error"
date: 2015-09-17
forum: Networking &amp; Wireless
---

### Post by janeku2 on 2015-09-17
Hello people,
I have issue with sharing files and documents over network.
My PC where is installed 14.04.LTS 32-bit has shared folder with SMB where access is to local users only.
From Windows access to files made with Open office and Libre office is OK, but from Ubuntu 15.04 I had problem :
Whenever I try to open I got this message:General input/output error while accessing /run/user/1000/gvfs/smb-share:server=.....
Please see attached image of this situation.
Any one could help to solve this issue ? 
I tried to search for it but no result at all.
Waiting for good Samaritian to help me solving this problem.
With regards,

---

### Post by tgalati4 on 2015-09-17
Look through the log files in /var/log/samba and see if you can find any obvious errors.  Post anything that might help troubleshoot this problem.  No need to post the entire log file, just the errors.

Basic SAMBA troubleshooting:  [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

Make sure the 15.04 machine belongs to the same workgroup as the Windows machines.  Only users in the same workgroup can share files--generally.

> tgalati4@Mint17 /etc/samba $ grep -e workgroup smb.conf
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


---

### Post by janeku2 on 2015-09-21
Hi,
Afyer installing samba I changed workgroup as it should be.
I must mention that other files like PDF or JPG could be opened without problem.
Main problem is dot, docx or similar files created with Libre Office or Open office.
Also changing all file properties to read-write status did not help solve this issue.

---

### Post by tgalati4 on 2015-09-21
I believe that LibreOffice creates "lock" files that prevents others from opening and editing the same file.  Do you have multiple users trying to open the same file?

---

### Post by bab1 on 2015-09-21
> **janeku2 said:**
> Hello people,
I have issue with sharing files and documents over network.
My PC where is installed 14.04.LTS 32-bit has shared folder with SMB where access is to local users only.
From Windows access to files made with Open office and Libre office is OK, but from Ubuntu 15.04 I had problem :
Whenever I try to open I got this message:General input/output error while accessing /run/user/1000/gvfs/smb-share:server=.....
Please see attached image of this situation.
Any one could help to solve this issue ? 
I tried to search for it but no result at all.
Waiting for good Samaritian to help me solving this problem.
With regards,
L.O. and OO both have problems working using the default GVFS (Gnome Virtual File System).  I have overcome the problems by mounting the share using the mount command directly using something like this```
sudo mount //server-name/share /some/mount/point/ cifs -o username=<user-name>,credentials=/home/<user-name>/.smbcred,uid=<user-uid>,gid=<user-gid>,nobrl
```

Or you can add the command to the fstab file and call it with a simple mount command like this```
mount /somemountpoint
```.  The fstab listing I use is this ```
//server-name/share-name cifs user,noauto,username=<user-name>,credentials=/home/<user-name/.smbcred,uid=<user-uid,gid
=<user-gid,nobrl  0  0
```

The most important option is nobrl.  The smbcred file has the *_user-name user-password _*in it.

---

### Post by janeku2 on 2015-12-06
Hello,
The problem was extended usb cable

---

### Post by Dr_Nik on 2016-05-25
Hi BAB1,
I'm new to Ubuntu as I just installed 16.04 LTS 64-bit on a spare laptop (played around with some earlier versions but never tried to access a network share on a Windows PC before). I've been able to solve most of my issues with google searches, but this one has been difficult to resolve. I have a Win 10 Pro 64-bit machine configured as a Home Media & Backup Server with Network Shares and their Permissions set for local accounts on this server. On my Ubuntu laptop I installed CIFS and was able to successfully mount network shares on my Win 10 PC. The only files I can't open are those managed by OpenOffice 4.1.2 (I removed Libre Office). I get the error mesage "General input/output error while accessing /run/user/1000/gvfs/smb-share:...

I opened the smb.conf and verified the "workgroup = WORKGROUP", that is the same as on my Win 10 PC. I also added the "name resolve order = bcast host".  This did not resolve my problem. I also looked in /var/log/samba but this directory is empty. In your examples above you mention about using the mount command or changing the fstab file. I know what my server-name & share-name are, but I'm unclear when user-name is for the Ubuntu account or the local account on Win 10.  I would appreciate any detailed examples or cifs advice you can offer for my setup.  Thanks!

---

### Post by Dr_Nik on 2016-05-27
I found an excellent CIFS guide in [http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/#comment-3521858](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/#comment-3521858) that solved all of my gvfs errors with OpenOffice trying to open files on my Windows Shares.  After following these procedures OO had no problems opening, creating its lock file, changing, and saving files on my Win Shares.  I am a software engineer, but quite new to the Ubuntu Linux world and trying to research all the smb, cifs, & gvfs manuals can be a huge task. I hope this url helps others that have this same problem.

---

