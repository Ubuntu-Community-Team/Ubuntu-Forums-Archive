---
title: "Cannot Share Removable Hard Drive"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by starwarsfan982 on 2006-09-08
Hi, This is my first time on the forums but I have been using Linux for about a year and a half. I am having some trouble getting my removable hard drive to share on the Samba Network we have setup. I have set it up to share, and it is browseable, available, and public. What am I doing wrong? PLEASE HELP!!

Dylan

---

### Post by tbonius on 2006-09-08
Define your trouble?

What file system is on your Removable Drive?  Does the Linux kernel have write access to it?  What does your smb.conf look like for this particular defined SMB share?  Where is it mounted?  Is the file system/directory where it is mounted chmod'ed so that users can read/write/execute?  Does the SMB browser on the remote computer even show the sharename (not the actual share) as present?  What type of error do you get when you try and access it?

T

---

### Post by starwarsfan982 on 2006-09-09
> **tbonius said:**
> Define your trouble?

What file system is on your Removable Drive?  Does the Linux kernel have write access to it?  What does your smb.conf look like for this particular defined SMB share?  Where is it mounted?  Is the file system/directory where it is mounted chmod'ed so that users can read/write/execute?  Does the SMB browser on the remote computer even show the sharename (not the actual share) as present?  What type of error do you get when you try and access it?

T

I am not sure of how to find out what type of fs is on the removable drive. I have write access to it. It is mounted on /media/SEA_DISC and when I access it on the windows browser it says to contact your admin to see if you have access to this folder and then says network access is denied. Whenever I try to CHMOD the proper commands and then check them in nautilus, it still forbids anyone but the owner to read, write, or execute. The smb.conf file has nothing written in it.

---

### Post by tbonius on 2006-09-09
So are you trying to share this removable drive with SMB to other Windows machines?  If so you need to setup your smb.conf file to share out that directory where the drive is mounted.

T

---

