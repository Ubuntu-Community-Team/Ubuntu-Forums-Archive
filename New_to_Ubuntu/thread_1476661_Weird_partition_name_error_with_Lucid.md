---
title: "Weird partition name error with Lucid"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by butsuriboy on 2010-05-08
Update:
So far, things have been an educational experience :), but sadly, my minor oddity's gotten worse.  Now, I can't mount/ unmount my windows partition without (as best as I know) going to the terminal and doing a sudo mount command.  Any and all help to get ubuntu working again would be much appreciated!

Thanks in advance!
---------------
Hi,
    I have a Windows XP partition also installed on my hard disk, and I believe it was mounted when I updated from 9.10 to 10.04.  Now, ubuntu has renamed the drive (or should I call it the partition?) to E840DF1040DEE47A_ with the underscore at the end, when previously, it did not have the underscore.  This has caused all my music files in my library for Rythmbox to no longer point to the correct location (as well as some launcher's I'd placed on my desktop to quickly access certain folders within the windows partition).  It's not that hard for me to just delete all my files in Rythmbox and have it re-find them, but I figured I'd try to learn a little more about what's going on :)

So, is there a way for me to get Ubuntu to re-name the partition to E840DF1040DEE47A ?  Also, as I've been digging around, I've noticed that when I mount the partition, it seems to place a folder in the /media/ folder, and weird thing, there is already a folder called /media/E840DF1040DEE47A there!  I try to open it, and I get an error message telling me the contents can't be displayed because I don't have the proper permissions for that.  So, I'm suspecting Ubuntu thinks that drive is still mounted?

Thanks for all your help!
PS, I did do some reading on the forums, and I can't seem to find anyone else that's had this same issue.  I know this may be purely speculation, but any idea why it might just be me? :)

---

### Post by dagdeniz on 2010-05-08
i think it's related to the fstab entry for the partition. if there is the entry for the partition in fstab, change the permissions (under the row <options>) to "user,auto"; or if you wanted it not to be mounted automatically, "user,noauto"

if there is not any entry for it, firstly (if you don't know) you should find out the number of the partition by typing ```
fdisk -l
``` in the terminal, then edit fstab by typing ```
sudo nano /etc/fstab
```
the fstab entry for the partition should be something like this, question mark being the partition number: 
```
/dev/hda?        /media/E840DF1040DEE47A  ntfs   user,noauto     0       0
```

---

### Post by butsuriboy on 2010-05-08
I do > fdisk -l and it does nothing.  Is there a part of the command I'm missing?

---

### Post by dagdeniz on 2010-05-08
ah, sorry, i need some time to get accustomed to ubuntu:) try: 
```
sudo fdisk -l
```

---

### Post by butsuriboy on 2010-05-08
I tried that, and got
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc23cc23c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13447   108012996    7  HPFS/NTFS
/dev/sda2           13448       14593     9205245    5  Extended
/dev/sda5           13448       14538     8763426   83  Linux
/dev/sda6           14539       14593      441756   82  Linux swap / SolarisI then went into fstab, but saw
>  
GNU nano 2.2.2              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=52d05ace-0b31-4ad9-a1dc-2bbf4bf61a56 /               ext3    relatime,erro$
# /dev/sda6
UUID=7dc2d0bc-602c-41dd-bba5-0254b4869dab none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

so I don't see the E840DF1040DEE47A listed (or, sda1 for that matter).

Also, I don't know if this helps, but everything I'd mentioned in my first post, I did with Nautilus.
Also, I'm a little worried I may have deleted the last character or so from fstab, as I was trying to figure out how to get out of that menu.  Any way to check?

Thanks again!

---

### Post by dagdeniz on 2010-05-08
it seems that you haven't deleted anything (cdrom, swap and linux are still there). now, what you should do is to add the line for the ntfs partition at the end of the file, again by typing 
```
sudo nano /etc/fstab
```. it should be like this:
```
/dev/sda1      /media/E840DF1040DEE47A  ntfs   user,noauto    0            0
```
after that, press ctrl+O to save the file (and of course "enter" after that to confirm) and ctrl+X to quit, and it should be done.

---

### Post by butsuriboy on 2010-05-08
Ok, I'll try that.  Just curious, though, what exactly is this doing?

---

### Post by butsuriboy on 2010-05-08
Ok, I did that, and it still lists /media/E840DF1040DEE47A as an inaccessible folder, and /media/E840DF1040DEE47A_ as an accessible folder (I currently have the windows partition mounted).

So again, what did the fstab stuff do, and any other ideas?

Thanks again!

---

### Post by dagdeniz on 2010-05-08
strange... for "what does it do", fstab lists the mountable devices on your system. the first part indicates which partition you want to mount (it is either indicated by an UUID number, or partition number -like sda1- or both), the second part is where you want to mount it (we say, in the /media/xyz folder), the third part is the filesystem (we said, ntfs), the fourth part is the options part ("user": user can open, "noauto": but not automatically mounted), the fifth, I dunno :), the last if the password is required or not, we said "0", that's no. 

i don't know a further solution but try this; unmount the partition if it's still mounted (in nautilus, in the left, right click on the partition and unmount). After doing that, type ```
gksudo nautilus
``` in the terminal. this will open nautilus with root privileges. Navigate to  /media/E840DF1040DEE47A and try to open it. Still not opening? (I'm asking you to do so to understand if it is about the privileges or about the mounting point)

---

### Post by butsuriboy on 2010-05-08
Ok, this is pretty weird.  So, I did as you asked, and the Sudo nautilus did allow me to access the /media/E840DF1040DEE47A folder.  When I did, I noticed the "drive icon" for that partition showed up on my desktop.  I tried unmounting from there, and it wouldn't let me (again, citing lack of permissions).  I then tried umounting the folder (in /media) from the sudo nautilus, and it seemed to work, but there's still a folder called E840DF1040DEE47A in media that the sudo nautilus says is empty.  Right clicking gives me the option to unmount, but when I try, it says
> umount: /media/E840DF1040DEE47A: not mounted

So, I've tried to remount from the Places menu, and it says
> Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)


So, it looks like I somehow lost permissions to mount the partition?  I try to mount through the sudo nautilus, and it won't let me go to the computer:/// where I'd normally (under normal nautilus) be able to see the drive and mount from there

---

### Post by dagdeniz on 2010-05-08
As I've told you, I can't guess further what's wrong but apparently it's about how fuse and ntfs-3g (the apps that make us be able to read and write ntfs in linux) is build in ubuntu 10.4; and that's beyond my little knowledge and experience. However, till someone posts a solution, you can manually unmount and mount that partition (with root privileges) so that Rythmbox will work as you want it to work. Here is how you mount it:

```
mount /dev/sda1 /media/E840DF1040DEE47A
```
If it's mounted in "/media/E840DF1040DEE47A_", you must first unmount it to be able to do this.

---

### Post by butsuriboy on 2010-05-08
Ok, thank you so much for you help dagdeniz!  And I hope there are other people out there that can help with this :P[]("http://ubuntuforums.org/member.php?u=944663")

---

### Post by butsuriboy on 2010-05-08
bump

---

