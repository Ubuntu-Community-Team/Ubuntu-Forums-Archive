---
title: "Problem opening Samba shares on Windows."
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by hellmet on 2007-12-08
I've a nice strange problem here, that may not be strange to some. Please try and help me out.

Installed samba, changed security to share. Put 
/media/FA1   -- my external hdd
/media/hda5  -- my internal hdd not the ubuntu partition. Fat32
/home/sanju  -- my home directory

on Samba share.

Test on a Windows XP laptop and a Windows Vista laptop.

Only /home opens. Other folders spit out an error
"This share is not accessible, contact administrator and check if you have right permissions"

Am I doing something wrong?

Thanks for your time.

---

### Post by hellmet on 2007-12-09
Ok.. I reboot the Vista into Ubuntu, and try to access the shares. Same thing. Was able to access /home , but not the others. Check attachment to see the image.

---

### Post by davidgarcin on 2007-12-09
Can you post your /etc/samba/smb.conf ?  There's a little more to it than changing security to share, but you're on the right track.

Also, have a look at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

What kind of access are you trying to give?  Read?  Read/Write?  Authenticated?

-David

---

### Post by hellmet on 2007-12-09
Thank you for your response.

I've attached smb.conf.

I only want the files to be read-only.. I have lots of videos and movies, that I'd be able to access across other computers.

---

### Post by davidgarcin on 2007-12-09
OK, so what you want is read-only public non-authenticated access.  Here's the relevant how-to:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

You have six entries in smb.conf.  To share those three directories, you only need the three that you want to share.  These entries should be of the form

```
[FA1]
  path = /media/FA1
  guest ok = yes
  read only = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup
```

you also have to set the permissions of the folder to 777 with this command:
```
sudo chmod -R 777 /media/FA1
```

In your first post you say you have your home directory at /media/(user)/home, which is a little strange, typically it's /home/(user)  and that's actually what your smb.conf says as well.

Once you've edited your smb.conf, restart the Samba server with:
```
sudo testparm
sudo /etc/init.d/samba restart
```

EDIT: You will find the entries at the bottom of the smb.conf.  Edit it with sudo gedit /etc/samba/smb.conf

---

### Post by hellmet on 2007-12-09
Oops, sorry. It is /home/sanju . 
Thank you. I'll try and let you know.

---

### Post by hellmet on 2007-12-09
Ok. I did what you said. But, chmod doesn't work. The command doesn't return errors, but the  permissions don't change. When I do 'sudo nautilus'  and try doing 777 permissions, it doesn't allow me to. It comes back to the defaults.
One thing I can't understand is how /home/sanju is accessbile, while others are not!!

---

### Post by davidgarcin on 2007-12-10
Sorry for the delay in responding.

Could you post your /etc/fstab ?  It sounds like the way the volumes are mounted will not let you change the permissions.

Also post the output of ```
ls -l /media
```

---

### Post by hellmet on 2007-12-10
Not a problem. More than happy to receive help.
Fstab :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f5c17495-d2e9-43e4-8718-83558ab30a62 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=C94F-B717  /media/XP       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=0F59-05B1  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=5070-70A0  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

ls -l /media

```
total 180
lrwxrwxrwx  1 root  root        6 2007-10-19 05:57 cdrom -> cdrom0
drwxr-xr-x  2 root  root     4096 2007-10-19 05:57 cdrom0
drwx------ 22 sanju root    32768 1969-12-31 18:00 FA1
drwx------ 92 sanju root    32768 1969-12-31 18:00 FA2
drwx------  2 root  root     4096 2007-11-12 10:26 FA3
drwx------ 14 sanju root    32768 1969-12-31 18:00 FA3_
lrwxrwxrwx  1 root  root        7 2007-10-19 05:57 floppy -> floppy0
drwxr-xr-x  2 root  root     4096 2007-10-19 05:57 floppy0
drwxrwx--- 52 root  plugdev 32768 1969-12-31 18:00 hda5
drwxrwx---  8 root  plugdev 32768 1969-12-31 18:00 hda6
drwxr-xr-x  2 root  root     4096 2007-10-24 08:57 mountt
drwxrwxr-x  2 root  root     4096 2007-10-19 05:57 XP

```

---

### Post by davidgarcin on 2007-12-16
OK, yeah, those partitions will automatically be mounted with root as the owner, and that's why you can't change the permissions.  I have the same thing on my comp, but I didn't realize it.

In your fstab, the line that follows prevents nobody users (which Samba uses for remote un-authenticated users) from accessing the files:

```
UUID=0F59-05B1  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```

Specifically, if you change the "umask=007" to "umask=0000", that will give full permissions to nobody users.  Samba, however, should limit the access to read-only, if I understand things correctly.  So change those lines in your fstab, then unmount/remount with the commands below, and it should work.  I'm not entirely sure why you need to give full permissions to the nobody user, not just read, but that's what a lot of how-to's say.  If you're concerned about security, you might try using umask="0003" and seeing if it works.  Maybe someone else can clear up this point.

```
sudo umount /media/hda5
sudo mount -a
```

I'm also noticing that you don't have an entry for FA1 in your fstab.  Do you mount that manually, or was it not plugged in when you viewed the fstab file?

---

### Post by zzztownsend on 2008-02-02
davidgarcin

very useful post, thanks - fixed this problem for me - I have a vfat partion mounted within my home folder. I could get most of the the home folder to share but nothing within the vfat mount.

Cheers 

Matt

---

