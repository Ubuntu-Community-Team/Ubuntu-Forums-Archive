---
title: "SOLUTION: Connecting to network shares"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by TonyS on 2008-05-19
Gidday all,

My skill level in this area amounts to "gormlessly follow the how-to guides", so if that's you too, this might be just what you've been looking for!

Ever since installing Hardy I've been having no success mounting network shares at bootup correctly.

When upgrading from Gutsy the existing fstab entries suddenly created weird permissions problems, where the drives would appear on the desktop, but their contents could not be displayed, or could but I was locked out of opening most of the contents.

The solution has finally been FOUND. I didn't do this work (its in a bug report and elsewhere in the forums) but because I've seen so many people hunting for the answer I though reposting it might help somewhere.

Most how-to guides you see here or elsewhere on the web (in my case the old "Unofficial Guide to Dapper") explain how to edit fstab and make an entry similar to this (in this case to mount a drive called "fred" located on a server at 192.168.0.100):-

//192.168.0.100/fred    /media/fred smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

The WORKING equivalent under Hardy is this:-

//192.168.0.100/fred    /media/fred        cifs    credentials=/root/.smbcredentials,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

The key changes are the use of the built-in cifs instead of the now-depreciated smbfs, and the apparently-essential "nounix" switch.

Follow the rest of the normal instructions for creating the local mount folder (in this example "mkdir /media/fred"), creating the credentials file etc in exactly the traditional way.

Good luck!

Cheers,

Tony

---

### Post by dmizer on 2008-05-19
thanks.  linked to this thread from my howto here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by bobd72 on 2008-06-02
Thanks TonyS. After numerous queries on numerous forums you have solved my Hardy problem. Interesting that my Desktop Hardy machine works without the 'nounix' option, but my laptop requires it.

Initially I thought this resolved my problem - not so:-(  Laptop still will not connect to the share. mount -t cifs will connect successfully but neither mount.cifs nor your fstab solution will mount the share???

---

### Post by techstop on 2008-06-09
Thanks Tony, going a little batty trying to get a share mounted that worked perfectly in the last 4 versions of ubuntu!

---

### Post by SoundFriend on 2008-09-06
I've got the same problem, I can't get the Fstab server share to mount in Hardy.

My fstab line is:
> 
//chef/sharename /media/sharename cifs guest,rw,nounix,iocharset=utf8, file_mode=0777, dir_mode=0777 0 0


I get the error:
>  CIFS VFS: cifs_mount failed w/return code = -22  
when I then try mount -a  

D'oh!  Fixed the problem.  The error code indicated that smbfs was not installed!

John

---

### Post by gush on 2010-01-26
Hello,
I have the following problem, I can mount it ok, I wrote this on my fstab:

```

//server/www /media/www cifs rw,user,credentials=/root/.smbcredentials,iocharset=utf8,dir_mode=777,file_mode=777 0 0

```

but I need normal user permissions to enter the /media/www
as I can just access to /media/www with the root user

Any help?
Thanks in advance.

---

### Post by dmizer on 2010-01-26
> **gush said:**
> Hello,
I have the following problem, I can mount it ok, I wrote this on my fstab:

```

//server/www /media/www cifs rw,user,credentials=/root/.smbcredentials,iocharset=utf8,dir_mode=777,file_mode=777 0 0

```

but I need normal user permissions to enter the /media/www
as I can just access to /media/www with the root user

Any help?
Thanks in advance.

See the second link in my sig. In the troubleshooting section there are several fixes for "Files owned by root"

---

