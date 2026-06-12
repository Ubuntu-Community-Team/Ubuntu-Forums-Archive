---
title: "Acess vista harddrive via ubuntu?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by UbubtuNewbie on 2010-09-07
Im gonna start by saying iv never used ubuntu before and im not great with computers in general :p 
I have windows vista installed on my pc, it crashed yesterday and i cant get into windows or acess any of my files. iv tried safe mode, system repair/restore off windows disk and everything else but nothing works. some1 told me i can get all my files off my harddrive through ubuntu then reinstall windows. Iv tried following some online tutorials on how to do this and i cant work it out. If i try to acess my hard drive in ubuntu it gives me 'You do not have the permissions necessary to view the contents of "disks-conf-sda1".' 
Any help would be greatly appreciated. thanks

---

### Post by Christian Knudsen on 2010-09-07
Perhaps this can help:

[http://ubuntuforums.org/showthread.php?t=1204763](http://ubuntuforums.org/showthread.php?t=1204763)

> To summarize(might help somebody)

first unmount it
sudo umount /dev/sdXX

make a folder where it will mounted on
sudo mkdir /media/Windows

get the uid of the partition
sudo blkid

backup the /etc/fstab which be configure later
sudo nano -Bw /etc/fstab then press Ctrl+O and Ctrl+X or just cp it

edit the fstab
sudo gedit /etc/fstab

add the following lines
# /dev/hda1 (this is just for comment)
UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,uid=1000,gid=1000,umask=000,fmask=137,u tf8 0 0

---

### Post by mapes12 on 2010-09-07
Once the Live Ubu CD has booted go Applications>Accessories>Terminal ```
gksudo nautilus
``` and hit enter. It will ask for your password. Type it in (nothing will show on the screen) and hit enter. The Nautilus file browser will launch with super user permissions i.e. access rights should not be restricted. If you can then get to your stuff, back it up onto whatever and away you go for your fresh install of windoze (but personally I would click the "install" icon to install UBU and ditch windoze).

):P

---

### Post by Mark Phelps on 2010-09-07
You would do better accessing the Vista OS partition on an as-needed basis through Places, rather than automounting it in your fstab.

One unclean shutdown and Vista will be rendered unbootable.

And, since ntfsfix can only fix SOME NTFS problems, if you then can't boot into Vista to fix it, Vista then becomes inaccessible.

---

### Post by coffeecat on 2010-09-07
> **UbubtuNewbie said:**
> If i try to acess my hard drive in ubuntu it gives me 'You do not have the permissions necessary to view the contents of "disks-conf-sda1".'

You shouldn't be getting a permissions error when trying to access a Windows NTFS partition through the Places menu. What did you do to get that?

This is what you need to do. Boot up with the Ubuntu live CD (I assume you haven't installed Ubuntu to your hard drive - your post isn't clear). Once in the desktop, at the top of screen you will see the Places menu. Somewhere in that menu will be your Vista partition - I can't tell you the exact name because this varies from system to system. If you click on it, a file browser window should open and then if you plug in a USB drive, you can do a straightforward drag and drop copy.

You do **not** need to create a folder and mount it in /etc/fstab. You do **not** need a gksudo nautilus file browser. However, if the Vista partition filesystem is corrupted, this may be the reason for the error message you see. If this is so, messing about with mountpoints and/or gksudo nautilus **will not help**.

It is really very simple copying files off a Windows partition with an Ubuntu live CD. You don't need complicated howtos. Just follow my second paragraph. If you do get an error message or you can't find your Vista partition in the Places menu, then post back with details and we'll take it from there. Good luck! :)

---

