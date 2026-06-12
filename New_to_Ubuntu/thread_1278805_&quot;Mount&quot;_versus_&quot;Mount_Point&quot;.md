---
title: "&quot;Mount&quot; versus &quot;Mount Point&quot;"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by BobJam on 2009-09-30
I'm having trouble understanding the difference between "mounting" and "mount point".

I need to understand this, because I want to make backups of my "/" and "/home" partitions, using PartImage, and store them on partitions I've created on my internal HDD specifically for these backups.The origin of my troubles understanding this is in this sentence on the psychocats page about PartImage ( [http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage) ):[INDENT]"In my case, I'm going to have to create a ***mount point*** (/backup) and then ***mount*** (**[COLOR=Blue]*my emphasis*[/COLOR]**) /dev/hda5 on the mount point."  (My partition for the "/home" backup is /dev/sda7).
[/INDENT]I had thought that all I would have to do was go into nautilus and create a /backup folder on each of the partitions I had created for the backups (BTW, I created the new partitions using Gparted on a "System Recovery CD" . . . not a LiveCD as instructed in the psychocats page . . . now I'm wondering if there would have been any difference if I had used a LiveCD).  But when I navigated to the partition, the File>Create Folder menu item was grayed out.  So I thought that maybe if I ran nautilus as root ("gksudo nautilus"), **THAT** would work.  It didn't . . . same result as nautilus not gksudo'd.[INDENT] [COLOR=Red]***<digression>***[/COLOR] Nautilus from "gksudo" produced some confusing results.  A few times when it ran, the backup partitions showed up in the side pane.  One time only the "/" backup partition showed up.  And other times, NEITHER of the backup partitions showed up.  I ran "sudo nautilus" and got the same results.  Nevertheless, when either of the backup partitions showed up, the File>Create Folder menu item was grayed out.

Another confusing result here.  Whenever I ran nautilus NOT sudo'd (i.e. as the Home user, or in "normal mode" I guess you would say), it consistently showed BOTH backup partitions I had created (I also created KDE root and home partitions . . . all free space for now, but I want to 'speriment with Kubuntu and have been told to keep it seperate from GNOME . . . and nautilus in normal mode showed those partitions too, but nautilus sudo/gksudo did not).

And there was another result that confused me.  All four newly created partitons have a "lost+found" folder.  And they are empty (I opened those folders the few times the partitions showed up in root nautilus).  Why were the "lost+found" folders created on the new partitions, and what is "lost+found"? [COLOR=Red]***<end digression>***[/COLOR]
[/INDENT]So, my main question is "How do I create a /backup 'mount point' and then how do I 'mount' my /dev/sda7 partition on the mount point"?

I've googled this issue, and only get more confused than I already am.  Can somebody put this in plain English for me, maybe with some CLI or GUI "click here, click there" instructions?

---

### Post by Cheezespread on 2009-09-30
As I understand from the  pyschocats tutorial :

1. You need to backup your  "/home"  partition.
2. The space where you want it to backed up is /dev/hda7
3. We are just mounting the " /dev/hda7 " parition on /backup to access it as any normal mount . 

 So in the end /backup is your " /dev/hda7 " which is mounted to Linux so that you can access that particular partition.

Mounting - The process of making other partitions/drives ( CD , Floppy ) available in Linux . May be an external drive like in this example.

Mount point - The place or location where you can access these mounted partitions from . /backup here serves as " /dev/hda7".


_CLI for creating the mount point ._
1.Creating the mount point folder
```
sudo mkdir /backup
``` ( a folder named backup is created in " /" . )
2.mounting the /dev/hda5 partition on /backup

_NTFS partition_
```
sudo mount - t ntfs-3g /dev/hda7 / backup - o force
```  
_ext3 partition_
```
sudo mount - t ext3 /dev/hda7 / backup - o force
```

The syntax is like this :

mount -t <type of partition > <partition to mount > < mount point >

---

### Post by lisati on 2009-09-30
Have a look here: [http://en.wikipedia.org/wiki/Mount_%28computing%29](http://en.wikipedia.org/wiki/Mount_%28computing%29)

It might help if you imagine an older computer which uses tapes: mounting the tape means making the tape accesible to the computer (by physically putting it on the tape drive), and the "mount point" is the way of referring to the tape once the computer recognizes that it's there.

---

### Post by snakeman21 on 2009-09-30
Let's say you have a USB stick.  When you plug it into a computer, the computer assigns it a path, such as /dev/sdb.  That path is the mount point, the virtual "location" of the flash drive.  This means that the drive is mounted at /dev/sdb.

---

### Post by Bachstelze on 2009-09-30
> **snakeman21 said:**
> Let's say you have a USB stick.  When you plug it into a computer, the computer assigns it a path, such as /dev/sdb.  That path is the mount point, the virtual "location" of the flash drive.  This means that the drive is mounted at /dev/sdb.
No. /dev/sdb is the device name of the drive. The mount point is somewhere else.

---

### Post by philinux on 2009-09-30
+1 the mount point is likely to be /media/diskx.

/dev/sdb on my rig refers to my second internal drive. I suppose it depends on what was plugged in on system install too.

---

### Post by Paqman on 2009-09-30
"Mount point" is a noun, it's the location within the filesystem that you want you data on. "Mount" is a verb, it's the act of getting that data into that mount point.

The mount point is just a location you create ready for mounting stuff onto. The actual mounting is done through a command (often put into /etc/fstab to automate it)

---

### Post by snakeman21 on 2009-09-30
> **Bachstelze said:**
> No. /dev/sdb is the device name of the drive. The mount point is somewhere else.

Oops, sorry.  I get the two confused, but you are right, the mount point would be /media/disk or /media/name_of_drive.

Sorry about that.

---

### Post by slakkie on 2009-09-30
Mount is the device being mounted on a specific location, which is the called mount point.

/dev/sdb1 is the mount, /home is the mount point.

Mounting is done via the mount command:

```

mount /dev/sdb1 /home

```

The mount can also be a network share (samba/nfs/etc).

```

#Samba share in this case
mount -t cifs \\xxxxx.euronet.nl\homes /mnt/samba/home

```

If you have it defined in your /etc/fstab you can omit some bits:

```

# fstab entry
\\xxxxx.euronet.nl\homes                /mnt/samba/home cifs    user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

```

```

mount /mnt/samba/home 

```

and it will mount \\xxxxx.euronet.nl\homes on /mnt/samba/home as defined in /etc/fstab.

For more information:
man mount
man umount

---

### Post by snakeman21 on 2009-09-30
> **slakkie said:**
> Mount is the device being mounted on a specific location, which is the called mount point.

/dev/sdb1 is the mount, /home is the mount point.

Mounting is done via the mount command:

```

mount /dev/sdb1 /home

```

The mount can also be a network share (samba/nfs/etc).

```

#Samba share in this case
mount -t cifs \\xxxxx.euronet.nl\homes /mnt/samba/home

```

If you have it defined in your /etc/fstab you can omit some bits:

```

# fstab entry
\\xxxxx.euronet.nl\homes                /mnt/samba/home cifs    user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

```

```

mount /mnt/samba/home 

```

and it will mount \\xxxxx.euronet.nl\homes on /mnt/samba/home as defined in /etc/fstab.

For more information:
man mount
man umount

Well said.

---

