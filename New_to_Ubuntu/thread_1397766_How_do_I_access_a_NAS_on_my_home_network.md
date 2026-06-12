---
title: "How do I access a NAS on my home network?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by colinmccubbin on 2010-02-03
I have a NAS on my home network, at a static ip of 192.168.2.101 in my windows explorer it appears as drive z:

I've now added Ubuntu 9.10 as a dual boot, on my desktop pc and want to also access the files on the NAS if I have booted up into Ubuntu rather than win. 

In Ubuntu if I type [http://192.168.2.101/](http://192.168.2.101/) into my browser I get the admin page of the NAS.

And in the same browser window I can log into it, so I now want to mount it in my Ubuntu filesystem. Preferably at boot up.

I've spent several hours googling this and trying various author's suggestions but nothing works that I've tried.

1.  I've created a mount point in /media/NAS in my files system using **sudo mkdir /media/NAS**. This now shows up as an empty file.

2. I edited /etc/fstab   to add these lines:

# Mount the NAS drive
//192.168.2.101/public//media/NAS smbfs guest 0 0
[B]
3.I then ran [/B]sudo mount -a 

This fails with a **mount: mount point smbfs does not exist** message.

I'm stumped at this point so any help would be appreciated!

Thanks.:D

---

### Post by Iowan on 2010-02-03
Hope [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To will help.

---

### Post by audiomick on 2010-02-03
Another very useful thread from dmizer here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by colinmccubbin on 2010-02-03
> **Iowan said:**
> Hope [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To will help.

Thanks, using the example there, when I run this in a terminal, to manually mount the NAS:
```
sudo mount -t cifs //192.168.2.101/public /media/NAS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=077
```

I get the error message: 

```
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Googling that i can only find hits that say basically "This is not a Linux problem, but the Windows machine is the one that is
causing it and refusing to allow the mount." but my NAS is running linux...

---

### Post by colinmccubbin on 2010-02-03
> **audiomick said:**
> Another very useful thread from dmizer here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)


Interesting... dmizer's post starts off almost at once with:

[I]Problem 1:
Ubuntu is not able to browse shares in workgroups that it is not a member of. By default, Ubuntu is a member of the &#8220;WORKGROUP&#8221; workgroup, but not all Windows computers use this convention.[/I]


My home network is set up as workgroup  TYROLHOME  so I'm going to start by trying his problem 2 solution:

*edit /etc/samba/smb.conf in order to change the workgroup that Ubuntu is a member of.*

Later........................................................................

Did that.... stopped and restarted samba, then re-ran:

```
sudo mount -t cifs //192.168.2.101/public /media/NAS -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=077
```

Same memory error message...:icon_frown:

---

