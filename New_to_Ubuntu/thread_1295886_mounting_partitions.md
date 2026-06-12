---
title: "mounting partitions"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by patchido on 2009-10-20
well, i know this is possible ive read it somewhere, but cant really find it, what i need is to automatically mount a partition at startup, can someone plz help me :D

---

### Post by swoody on 2009-10-20
Have you read through the wiki on this subject?
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

If that doesn't get you squared away can you give us more details about the partition you're trying to mount? What filesystem, size, same or different hdd, etc. etc.

---

### Post by patchido on 2009-10-20
this is my fdisk, i dont want to mess up ubuntu, plz tell me what to do, in the wiki i didnt understand the part into "preparing the system" do i have to make a directory??

---

### Post by Zoot7 on 2009-10-20
What type file system is it? ntfs? ext3? ext4? and which partition?

Normally what you have to do is make a directory where you want to mount it (normally in the /media folder), then specify the file system, options and where to mount it in fstab. (/etc/fstab)

If you provide a few more details we'll be able to set it up for you. ;)

---

### Post by patchido on 2009-10-20
forgot to paste my fdisk sorry :)

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         673     5405841    7  HPFS/NTFS
/dev/sda2             674       14593   111812400    5  Extended
/dev/sda5             674        2569    15229588+  83  Linux
/dev/sda6           14023       14593     4586526   82  Linux swap / Solaris
/dev/sda7            2570       14022    91996191    7  HPFS/NTFS

```

---

### Post by patchido on 2009-10-20
i did create a directory in /media/Data

sda7 is the partition that i want to mount in media/Data automatically

---

### Post by Rayve on 2009-10-20
patchido,

If I understand the HowTo correctly, this should be the line you'd enter into /etc/fstab:

```

/dev/sda7   /media/Data   nfts   user,fmask=0111,dmask=0000   0   0


```To do so, you can edit /etc/fstab with your preferred text editor, for 
example, to use gedit:

```
 sudo gedit /etc/fstab 
```Note that for automounting, it may be best to use UUID= in place of 
/dev/sda7.  To do this, run

```
 sudo blkid 
```enter your password if sudo requires it, and then it will list all 
partitions and their UUIDs and labels, if applicable.  You'll want the
UUID= section of /dev/sda7 (it'll be a long string of letters and numbers
with dashes), but without the quotes.  You can enter that into the fstab 
instead of the /dev/sda7.

The HowTo does mention that if you want to write to that partition, 
since it's nfts, you may want to **install nfts-3g and then** (after that
is installed) put nfts-3g in place of nfts in that fstab line.

I'm just a beginner myself, but hopefully this gives you the right idea,
and others will correct anything I may have missed.  :)

Edited to add an example of /etc/fstab with the UUID -

```

UUID=a941fe4c-c29d-412e-a717-4edff3361398 /               ext3    relatime,errors=remount-ro 0       1

```
Where the file system is identified by the long UUID= string, the mount point is / or root, and the type is ext3, with then defaults (relatime, etc), dump and pass options.

---

### Post by patchido on 2009-10-20
well, i did this, it seems to be mounted but if i click into places then data, i get this


"The volume 'Data' uses the  file system which is not supported by your system."

---

### Post by Zoot7 on 2009-10-20
Odd. Maybe the switches in fstab are incorrect, I'm not in front of my own Ubuntu installation so I can't confirm that.

Anyway, try this;
unmount it manually by doing
```
sudo umount -l /dev/sda7
```
and then mount it again by
```
sudo mount -t ntfs-3g /dev/sda7 /media/Data
```

See if that throws up an error, (it shouldn't) and post it here. Then try and access /media/Data.

---

### Post by patchido on 2009-10-20
i did the first, and it replied, not mounted, but the second command worked

---

### Post by patchido on 2009-10-20
so, what do i have to do to make it work?

---

### Post by howefield on 2009-10-20
You could try pysdm, installed with Synaptic Package Manager. 

Seems to make this pretty easy.

---

### Post by Zoot7 on 2009-10-20
> **patchido said:**
> so, what do i have to do to make it work?
Unmount it again and try adding this line to fstab
```

/dev/sda7 /media/Data ntfs-3g defaults,umask=007,gid=46 0 0
``` 
Then to test it do
```
sudo mount -a
```

---

### Post by Rayve on 2009-10-20
In How To fstab, a great HowTo by bodhi.zazen ([http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)) there is this line - 

> 

[LIST=1]
[*]/mnt Typically used for fixed hard drives HD/SCSI. [COLOR=darkred]If you mount your hard drive in /mnt it will NOT show in "Places" and your Desktop.[/COLOR]
[*]/media Typically used for removable media (CD/DVD/USB/Zip). [COLOR=navy]If you mount your hard drive in /media it WILL show in "Places" and your Desktop.[/COLOR]
[/LIST]
So... if you're mounting a partition of your hard drive, perhaps /mnt will work best?  Unless you want to see it in "Places" and on your Desktop, of course.

---

### Post by gareththegeek on 2009-10-20
When I added my ntfs partition into the fstab file I simply put

```
/dev/sda1 /mnt/windows ntfs
```

Didn't need the other options (which was handy because at the time I needed to access my ntfs partition in order to configure my internet in order to look up how to use the mount command :P)

---

### Post by patchido on 2009-10-20
solved :D thx

---

