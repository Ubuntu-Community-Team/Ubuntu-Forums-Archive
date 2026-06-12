---
title: "Mounting SMB shares at boot"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-02-21
Hi guys.

I have my fstab set to mount certain SMB shares at boot like so:
```
//familydesktop/c /media/familyc cifs iocharset=utf8,credentials=/home/family/.smbcredentials,uid=1000 0 0
//familydesktop/media /media/media cifs iocharset=utf8,credentials=/home/family/.smbcredentials,uid=1000 0 0
//familydesktop/music /media/music cifs iocharset=utf8,credentials=/home/family/.smbcredentials,uid=1000 0 0
```

When I do a *sudo mount -a* they all appear on the desktop and work marvelously. However at boot they do not appear, I'm guessing perhaps because the wifi is yet to be enabled when all the drives are mounted?

What can I do to make it automatically mount those drives.

---

### Post by Pas_sa on 2009-02-22
Bump..

---

### Post by Pas_sa on 2009-02-23
Does no one seriously know? :( it's really annoying me.

I tried setting the command to run at boot with the Sessions option but it still runs seemingly before the wifi connects so the drives dont appear until I run the command manually.

---

### Post by yther on 2009-02-23
I'm jealous of you because my SMB shares don't mount unless I give the IP address!  :(

For your mounting problem, try adding **_netdev** into your options.  So, for example:

```
//familydesktop/c /media/familyc cifs iocharset=utf8,credentials=/home/family/.smbcredentials,uid=1000,_netdev 0 0
```

That is supposed to tell the system to wait until networking is up before it tries to mount.  I use this on my laptop to mount some Windows shares at work, and it does the job.  Also if you are using OpenOffice to read MS files, you might want the **nobrl** option as well; it is supposed to fix a problem with Writer not opening .DOC files correctly.

Good luck and I hope this helps!

---

### Post by element_G on 2009-02-23
Following this 

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

is what got my Samba to automount

---

