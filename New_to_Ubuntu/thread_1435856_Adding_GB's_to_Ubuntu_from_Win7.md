---
title: "Adding GB's to Ubuntu from Win7"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by RCToTheFuture on 2010-03-22
I have my Ubuntu set up running out of space way to fast. I can't edit the Win7 partition to break off an extra 30GB's from its self in Ubuntu and add it onto the Ubuntu partition. If I were to go into Win7, break off 30 GB's and then add it to the Ubuntu one, would that cause any problems with Ubuntu or no?

---

### Post by Ozymandias_117 on 2010-03-22
I believe first time you boot Ubuntu after changing the partition size, it will run fsck - But after that everything should be peachy.

---

### Post by RCToTheFuture on 2010-03-22
> **Ozymandias_117 said:**
> I believe first time you boot Ubuntu after changing the partition size, it will run fsck - But after that everything should be peachy.

Not to be an idiot, but what is fsck?

---

### Post by Ozymandias_117 on 2010-03-22
It's the GNU/Linux equivalent to chkdsk

---

### Post by RCToTheFuture on 2010-03-22
I was actually just googling it, and it says that NTFS isn't supported, yet I only use NTFS. That won't cause any effect?

---

### Post by Ozymandias_117 on 2010-03-22
Your Ubuntu partition should be either ext3 or ext4. I don't think there is any way to install Ubuntu into NTFS. Unless you did a Wubi install?

edit: If you're unsure, post the output of```
sudo fdisk -l
```

---

### Post by RCToTheFuture on 2010-03-22
> **Ozymandias_117 said:**
> Your Ubuntu partition should be either ext3 or ext4. I don't think there is any way to install Ubuntu into NTFS. Unless you did a Wubi install?

edit: If you're unsure, post the output of```
sudo fdisk -l
```

I think I did. Here's the output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88060d05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12763   102409216    7  HPFS/NTFS
/dev/sda3           12763       19457    53775360    7  HPFS/NTFS
rc@ubuntu:~$ 

```

---

### Post by Ozymandias_117 on 2010-03-22
Looks to me like that is probably a Wubi install on a Windows machine with a recovery partition.

Give me a few minutes to see if I can find out about increasing HDD size on a Wubi install.

---

### Post by RCToTheFuture on 2010-03-22
> **Ozymandias_117 said:**
> Looks to me like that is probably a Wubi install on a Windows machine with a recovery partition.

Give me a few minutes to see if I can find out about increasing HDD size on a Wubi install.

Yeah, I don't remember if I did a Wubi install, but I probably did because that's when Win7 used to shut down every 2 hours.

And thanks for all the help man, I do appreciate it.

---

### Post by Ozymandias_117 on 2010-03-22
> Resizing virtual disks using LVPM (not necessary if you're transferring the install to a dedicated partition)

Run LVPM, and once the menu appears, select either "resizehome" (to resize the /home virtual disk) or "resizeroot" (to resize the / virtual disk).

Input the new size, in MB, of the virtual disk.

Wait until the program finishes creating a new disks file and copying files from original home disk file; it will pop up a final instruction window instructing to backup the original home disk file and renaming the newly created disk file

Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to home.virtual.disk (if you used resizehome) or system.virtual.disk (if you used resizeroot)

Reboot into ubuntu

You can try [this]("http://lubi.sourceforge.net/lvpm.html"). The instructions I pasted with some screenshots are at the bottom.

---

### Post by Ozymandias_117 on 2010-03-22
Try that, if you have problems, maybe someone else can help you. If not, I'll be back on tomorrow, but I have to go to bed now lol. 1:30 am... Classes at 7:30.... hmmm ;)

edit: In case you check back to the page, and just see this, the instructions are on the bottom of page 1 ;)

---

### Post by RCToTheFuture on 2010-03-22
Will definitely give that a try. Thanks for all the hard work sir!

---

