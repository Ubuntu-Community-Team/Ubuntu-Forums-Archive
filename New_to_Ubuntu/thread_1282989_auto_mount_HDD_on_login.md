---
title: "auto mount HDD on login"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by trikster_x on 2009-10-05
I am trying to make it so that my second internal HDD mounts on login, like my external drive does.  I have tried playing with fstab and mtab, to no avail.  Does anyone know how to do this?

I need the drive to mount on login because I keep my media files on that drive and if I forget to mount the device before opening rhythmbox, it removes all songs from the library, then has to rescan the drive to replace them.

---

### Post by khelben1979 on 2009-10-05
When I decided to mount my Windows drives (using NTFS) I just wrote this from an command line:

```
mount -t ntfs /dev/sdb1 /mnt/Film_Disc/
```

Then it keeps mounted on my system all the time and unmounts automatically (I think) when the system reboots.

Use the ```
man mount
``` if you feel uncertain on how to use it.

---

### Post by Cheezespread on 2009-10-05
Hi trikster_x

Can you post your fstab contents in here ?.

---

### Post by trikster_x on 2009-10-05
> khelben1979:

When I decided to mount my Windows drives (using NTFS) I just wrote this from an command line:

Code:

```
mount -t ntfs /dev/sdb1 /mnt/Film_Disc/
```

Then it keeps mounted on my system all the time and unmounts automatically (I think) when the system reboots

I have done this once before, problem is it does not mount automatically on login, and I have to run root privileges to make it work, which means I can't set it as a session command.

> Cheezespread:

Hi trikster_x

Can you post your fstab contents in here ?.

Here you go:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=3b5372e6-2f10-44e0-9851-df9036b27c48 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=96a3bbee-e1d1-48cb-894f-9c7f65d86fc5 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda5 /home ext3 nodev,nosuid 0 2
```

I removed everything I did from fstab and mtab, because it was causing some problems when I tried to mount the drive manually.

---

### Post by Elfy on 2009-10-05
You can use pysdm to add the necessary to your fstab 

[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by jarrah-95 on 2009-10-05
put the code above 
```

mount -t ntfs /dev/sdb1 /mnt/Film_Disc/

```
but change it to work for you (chainge the lines /dev/sdb1 and /mnt/film_disk to what you need/want) and add it to start up apps. (copy and paste it in the command box

---

### Post by tom66 on 2009-10-05
That won't work, because the command needs root permissions.

---

### Post by trikster_x on 2009-10-05
> **forestpixie said:**
> You can use pysdm to add the necessary to your fstab 

[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Cool, this worked.  Now to check the options it set in fstab and learn how to do modify it when I get my new HDD.  Thanks.

---

### Post by Elfy on 2009-10-05
Glad it helped.

In your quest ot learn how to modify the file this will come in handy I think - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by trikster_x on 2009-10-05
Thanks again.  That will help immensely.

---

