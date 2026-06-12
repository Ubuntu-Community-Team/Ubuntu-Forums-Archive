---
title: "smbfs vs cifs"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by DugieHowsa on 2007-06-24
I am experiencing some issues with a Windows share, and I am looking for the best way to handle it.

For the last week, I have been going back and forth between cifs and smbfs for mounting a networked Windows Share (Its actually a SimpleShare NAS).

I was able to mount it with the correct permissions as an smbfs mount, but system performance was not good.  Nautilus and other applications would hang, and a few times the system completely froze.  Here is the entry I used in the fstab:

//Fileserver01/NetShare /media/Fileserver01 smbfs user,rw,file_mode=0777,dir_mode=0777 0 0

I then tried a cifs mount.  Performance improved, but I wasn't getting the permissions I wanted.  I had read/write access to some files, but I couldn't create any new folders.  Here are two of the entries I tried in the fstab directory:

//Fileserver01/Netshare /media/Fileserver01 cifs auto,user,rw,gid=smbusers 0 0
//Fileserver01/NetShare /media/Fileserver01 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

All I am looking to do is mount this share so that all users have full control.  Here is how the root of the share currently looks with the 2nd cifs fstab entry:

dugiehowsa@Ubuntu:/$ ls -la /media/Fileserver01/
total 12292

drwxrwxrwx 12 root  root     0 2007-06-24 12:11 .
drwxr-xr-x  5 root  root  4096 2007-06-24 11:25 ..
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 Documents
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 HomeAudio
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 HomeMovies
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 Movies
drwxr-xr-x  4 35000 42000    0 2007-06-24 12:11 Music
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 Picture Frame
drwxr-xr-x 37 35000 42000    0 2007-06-24 12:12 Pictures
drwxr-xr-x  2 35000 42000    0 2007-06-24 12:11 TV
drwxr-xr-x 10 35000 42000    0 2007-06-24 12:11 Unorganized

---

### Post by mitch.c on 2007-06-25
> **DugieHowsa said:**
> 
For the last week, I have been going back and forth between cifs and smbfs for mounting a networked Windows Share (Its actually a SimpleShare NAS).

You definitely want to drop smbfs... it's known to be "severely broken", and is no longer supported by the Samba team: [https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

> **DugieHowsa said:**
> 
I then tried a cifs mount.  Performance improved, but I wasn't getting the permissions I wanted.  I had read/write access to some files, but I couldn't create any new folders.  Here are two of the entries I tried in the fstab directory:

//Fileserver01/Netshare /media/Fileserver01 cifs auto,user,rw,gid=smbusers 0 0
//Fileserver01/NetShare /media/Fileserver01 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
Try this /etc/fstab entry:
```
//Fileserver01/NetShare /media/Fileserver01 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
```
I usually don't use the 'guest' option, but prefer "credentials", so YMMV.

---

### Post by DugieHowsa on 2007-06-26
That did it!  The noperm flag made all the difference.  Many Thanks mitch.c!

For all to reference, here is my final fstab entry:

//Fileserver01/NetShare /media/Fileserver01 cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

In summary, use cifs, not smbfs.  Here is the man page of mount.cifs that lists all the available options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

---

### Post by mitch.c on 2007-06-26
Glad to help.

---

