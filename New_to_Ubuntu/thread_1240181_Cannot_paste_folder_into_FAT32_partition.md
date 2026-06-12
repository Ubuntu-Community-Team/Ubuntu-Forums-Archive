---
title: "Cannot paste folder into FAT32 partition"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by fleamour on 2009-08-14
My fourth partition is FAT32, but both dragging or copy/paste from home folder into said partition wont work.  Are there some permissions that need to be set?

---

### Post by credobyte on 2009-08-14
Partitions usually require chowning ..
```
sudo chown -R user:user /partition/mountpoint
```
[COLOR=Gray]** Replace user:user with your username ( eg. dainis:dainis ) and set the right path to your partition ( mount point ).[/COLOR]

---

### Post by ptn107 on 2009-08-14
fat16 & fat32 ownership and permissions must be specified during the mount proceedure.  They do not respond to chown/chmod commands.

```
man mount
```

---

### Post by halitech on 2009-08-14
just out of curiousity, how big is the folder you are trying to copy/paste?

---

### Post by superprash2003 on 2009-08-14
yea , i think there are issues where files over 2gb are not supported..

---

### Post by CatKiller on 2009-08-14
Could be file size, could be symlinks. FAT doesn't support symlinks.

---

### Post by fleamour on 2009-08-14
Erm it's a rich text document, so probably not all that big.

---

### Post by swerdna on 2009-08-14
You can make it writable in the mount command. The mount command can be either temporary (mount from the command line) or permanent (mount via fstab)

[LIST]
[*]command line:```
mount -t vfat -o umask=0000,utf8 /dev/sdax /path_to/mount_point
```
[*]fstab option 1:```
UUID=AD74-85CA     /path_to/mount_point     vfat     umask=0000,utf8     0 0
```
[*]fstab option 2:```
/dev/sdax     /path_to/mount_point     vfat     umask=0000,utf8     0 0
```
[/LIST]

Details and full background here: [HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubufat32.html")

---

### Post by bodhi.zazen on 2009-08-14
> **credobyte said:**
> Partitions usually require chowning ..
```
sudo chown -R user:user /partition/mountpoint
```[COLOR=Gray]** Replace user:user with your username ( eg. dainis:dainis ) and set the right path to your partition ( mount point ).[/COLOR]

This is a common mistake on these forums. You can not chown or chmod on a FAT or NTFS partition (they do not support permissions).

You have to un mount and re mount the partition.

You can use ntfs-config, see swerdna's post , or

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by credobyte on 2009-08-14
> **bodhi.zazen said:**
> This is a common mistake on these forums. You can not chown or chmod on a FAT or NTFS partition (they do not support permissions).

You have to un mount and re mount the partition.

You can use ntfs-config, see swerdna's post , or

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

When I first time removed Windows & installed Ubuntu, I left my extended NTFS partition untouched ( contained data ). Upon loging in, I wasn't able to use it - it was mounted and everything seemed to be "ok". In my case, only chown helped ( immediately ).
Not sure if it was just a temorary bug or something else that let me thought this, but .. that's what I did and what worked for me a while back.

At least we got an explanation, why it *shouldn't* work in that way :)

---

### Post by fleamour on 2009-08-15
First off all read this:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14]("http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14")

For Xubuntu users:

```
gksudo mousepad /etc/fstab
```

...to edit fstab.  Then:

```
sudo vol_id -u /dev/**sda4 (or your vfat partition here)**
```

...to find out the UUID of your vfat partition.  Then enter this txt below other UUIDs in open fstab window.

```
UUID=**Your UUID number** /media **(correct file path)**/sda4 vfat     umask=0000,utf8 0  0
```

Works upon reboot.  Vfat partition will auto-mount, enabling read/write.

---

### Post by fleamour on 2009-11-02
```
sudo vol_id -u /dev/sda4
```

This code no longer works in Karmic.  I get this error:

```
sudo: vol_id: command not found
```

I can copy files *from* FAT32 partition but *cannot* write to partition.

---

