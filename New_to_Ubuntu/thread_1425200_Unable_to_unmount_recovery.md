---
title: "Unable to unmount recovery"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by mayyang on 2010-03-08
Hello, I just recently installed Ubuntu 9.10 and I'm not that Linux savvy so you'll have to help me out and dumb down the language a little...

I was trying to access my windows partition so I installed that "NTFS Configuration Tool" thing...and didn't bother seeing how to use it...and just hastily clicked on things.  So now I guess it mounted a "Recovery" drive.

When I try to unmount it, it says, Unable to unmount recovery and umount: only root can unmount /dev/sda1 from /media/Recovery.

How do I unmount it? ...in the simplest language possible?

(I realize there are a lot of posts similar to this...but I couldn't find one that could answer my specific question/circumstances since I'm new this...)

Thanks.

---

### Post by rbc on 2010-03-08
Open terminal, and type:
*sudo umount /dev/sda1*

You may be prompted for your password, the input for which will not be displayed, but it is being entered. Press Enter

---

### Post by sandyd on 2010-03-08
> **mayyang said:**
> Hello, I just recently installed Ubuntu 9.10 and I'm not that Linux savvy so you'll have to help me out and dumb down the language a little...

I was trying to access my windows partition so I installed that "NTFS Configuration Tool" thing...and didn't bother seeing how to use it...and just hastily clicked on things.  So now I guess it mounted a "Recovery" drive.

When I try to unmount it, it says, Unable to unmount recovery and umount: only root can unmount /dev/sda1 from /media/Recovery.

How do I unmount it? ...in the simplest language possible?

(I realize there are a lot of posts similar to this...but I couldn't find one that could answer my specific question/circumstances since I'm new this...)

Thanks.

can you post the output of
```

cat /etc/fstab
```

---

### Post by garvinrick4 on 2010-03-08
> **mayyang said:**
> Hello, I just recently installed Ubuntu 9.10 and I'm not that Linux savvy so you'll have to help me out and dumb down the language a little...

I was trying to access my windows partition so I installed that "NTFS Configuration Tool" thing...and didn't bother seeing how to use it...and just hastily clicked on things.  So now I guess it mounted a "Recovery" drive.

When I try to unmount it, it says, Unable to unmount recovery and umount: only root can unmount /dev/sda1 from /media/Recovery.

How do I unmount it? ...in the simplest language possible?

(I realize there are a lot of posts similar to this...but I couldn't find one that could answer my specific question/circumstances since I'm new this...)

Thanks.
If it has a Label of recovery:  sudo umount /media/recovery

---

### Post by mayyang on 2010-03-09
> **rbc said:**
> Open terminal, and type:
*sudo umount /dev/sda1*

You may be prompted for your password, the input for which will not be displayed, but it is being entered. Press Enter

That worked.  Thanks, guys!

---

### Post by mayyang on 2010-03-09
Hm, actually, although it works, it reappears when I restart...how do I delete it permanently?

---

### Post by anthonyrossbach on 2010-03-09
I have had this, there is a file in your system, I forget what one, but it will mount any drives set in this file on startup. May be the first thing to look at, I use id for mounting all my drives on startup, just been a while but now I told you and someone who knows this file may be able to now tell you where it is.

---

### Post by sandyd on 2010-03-09
> **carlee said:**
> can you post the output of
```

cat /etc/fstab
```

^^
this.
DIY instructions...
```

gksudo gedit /etc/fstab

```
look for /media/recovery

change it to /media/[whaeveryouwant]

save it
```

sudo mkdir /media/[whateveryouwant]
```

change [whaeveryouwant] to something you would like to name it, for example, "windows"

---

### Post by undecim on 2010-03-09
> **mayyang said:**
> Hm, actually, although it works, it reappears when I restart...how do I delete it permanently?

Sounds like you added it to /etc/fstab

Press alt+f2 and type "gksu gedit /etc/fstab" and you should get a text editor with text similar to this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=047856bd-c99a-42a4-861e-901ee99853fd /               ext4    noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# /home was on /dev/sda5 during installation
UUID=ee5beda8-c33e-48ed-ad71-1c3ceb726571 /home           ext4    noatime,nodiratime,errors=remount-ro,data=writeback 0       2
# swap was on /dev/sda2 during installation
UUID=a96e4b88-33f3-41c3-8083-361f83bb6814 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Your will have a line that includes "/media/recovery". Find that line, delete it, and save the file. When you reboot, recovery shouldn't be there anymore.

---

### Post by anthonyrossbach on 2010-03-09
> **undecim said:**
> Sounds like you added it to /etc/fstab

Press alt+f2 and type "gksu gedit /etc/fstab" and you should get a text editor with text similar to this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=047856bd-c99a-42a4-861e-901ee99853fd /               ext4    noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# /home was on /dev/sda5 during installation
UUID=ee5beda8-c33e-48ed-ad71-1c3ceb726571 /home           ext4    noatime,nodiratime,errors=remount-ro,data=writeback 0       2
# swap was on /dev/sda2 during installation
UUID=a96e4b88-33f3-41c3-8083-361f83bb6814 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Your will have a line that includes "/media/recovery". Find that line, delete it, and save the file. When you reboot, recovery shouldn't be there anymore.

Yup that is the one, hope you can get it to work!

---

