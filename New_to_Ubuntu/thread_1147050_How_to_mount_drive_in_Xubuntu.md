---
title: "How to mount drive in Xubuntu?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Duskao on 2009-05-03
Like the title says... How do I mount my second hard drive in Xubuntu? In Ubuntu it was quite easy. Is there a graphical way or does it require the terminal?

---

### Post by dabang on 2009-05-03
To mount a drive use the 'mount' command:
```
sudo mount -t [FS] [DEVICE] [MOUNTPOINT]
```
Which means:

- FS = filesystem
==> if you want to mount a Windows partition it would be "ntfs" or "vfat" (FAT32), for a Linux ext3 filesystem put "ext3" in here

- DEVICE
==> this is the device name, for example "/dev/sda1" for the first partition on the first HD (try "sudo fdisk -l" to see your HDs/partitions)

- MOUNTPOINT
==> a directory somewhere in your filesystem, i.e. "/mnt" oder "/media/disk"

Don't know for GUIs in Xubuntu...

---

### Post by Elfy on 2009-05-03
Whatever you did in ubuntu you should be able to do in xubuntu.

---

### Post by Duskao on 2009-05-03
Hello forestpixie. In Ubuntu I could just click "Places" and it was shown there, so then I could just click it and it would mount itself on my desktop, but it is not there in "Places" for Xubuntu. When I installed Xubuntu I did a clean install and changed to Ext4 and left the swap file, but chose mount location as "/". Would that make any differenence? I know that when I used Kubuntu it was a bit tougher as well.

---

### Post by Elfy on 2009-05-06
Sorry lost the subscription here - I'm not sure that Thunar works the same as Nautilus in that respect.

You could if the drives you wish to are static mount them in fstab in which case they will be avialble mounted at boot.

---

### Post by halitech on 2009-05-06
have you tried pmount?

---

### Post by colormoon on 2009-05-06
You can find the other how to in [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

    * To mount Windows partition 

> sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

    * To unmount Windows partition 

> sudo umount /media/windows/

---

