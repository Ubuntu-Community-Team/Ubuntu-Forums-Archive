---
title: "Mounting all connected hard drives at boot."
date: 2009-12-03
forum: New to Ubuntu
---

### Post by jotto! on 2009-12-03
I think I have seen some code somewhere to enable all connected hard drives to be mounted at time of boot but cannot seem to find it now. Not too keen on having to type in password just to browse a drive.

Any takers?

---

### Post by yeats on 2009-12-03
This will probably be helpful for you:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Excedio on 2009-12-03
Quoted from [Smorgasbord.net]("http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/")
 
> if you want it to be permanent, you need to edit your filesystem tab file. Run the following command in terminal:
[SIZE=2][COLOR=#921a14]$ gedit /etc/fstab[/COLOR][/SIZE]
The text editor window will appear with the fstab file loaded up. You will see something that looks kind of like this:

[SIZE=2][COLOR=#921a14]# /etc/fstab: static file system information.
#
# proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdb1 /media/hdb1 ext3 defaults 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[/COLOR][/SIZE]
All you have to do is add a new line for the new drive…
I will add the following line to my fstab for my new drive:

[SIZE=2][COLOR=#921a14]/dev/hdd1 /media/linuxstore ext3 defaults 0 0
[/COLOR][/SIZE]
Just be sure to substitute both the name of my hard drive for yours (mine is hdd1, is yours hdc1 or another name?), and my mount point hame for yours. Then save the file.
Now you will have the new hard drive mounted and writable both every time you boot. In Ubuntu, you should find your new drive listed under your ‘Places’ menu. To make the hard drive show up right now, without rebooting – just reload your fstab file with the following command:
[SIZE=2][COLOR=#921a14]$ sudo mount -a[/COLOR][/SIZE]
Now you’re done! Enjoy your new storage drive in Linux!

---

### Post by ukripper on 2009-12-03
> **jotto! said:**
> I think I have seen some code somewhere to enable all connected hard drives to be mounted at time of boot but cannot seem to find it now. Not too keen on having to type in password just to browse a drive.

Any takers?
Depends on what filesystem-format drive you trying to mount automatically. For external/internal NTFS auto mounting at boot, there is easy config tool caled ntfs-config, all you need to do is to run it and check two boxes. But if you are trying to mount ext2/ext3/ext4 or any other linux partition you will need to to do it in fstab. 

Let us know which filesystem format your drive is and we can help you auto mounting it.

---

### Post by jotto! on 2009-12-03
sorry for the delay guys...

The drives I want to mount are all ntfs so the ntfs-config tool is the way to go for me1

Many thanks.

---

