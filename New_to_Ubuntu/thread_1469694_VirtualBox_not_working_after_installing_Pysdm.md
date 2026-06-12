---
title: "VirtualBox not working after installing Pysdm"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Greblok on 2010-05-02
Hi all.

I am a complete n00b when it comes to Linux, and having difficulties understanding some things.

I wanted all my harddrives to be mounted at startup, so I installed Pysdm, no changes made other than this.

I had VirtualBox running a Windows 7 installation on one of these drives (the image and storage set to a folder on sdb1).
This was working great untill I installed Pysdm (at least i believe this is the issue), and now, VirtualBox is unable to mount the drive image.

It seems Pysdm also made som other changes, since now I am not allowed to mount or unmount the drive without the use of pysdm, telling me that only root is allowed to mount and unmount this drive.

It's killing me and I want to take back the controll of my drives, and get VB up and running again. Tried to uninstall pysdm but as I later came to understand, this is just a GUI and the actual permissions are set elsewhere(?).

Can somebody help me with this issue?

As described, I am a total n00b when it comes to Linux so if you need any more info I will gladly post it when I know what you gurus need. :)
Thanks in advance. :)

---

### Post by Paqman on 2010-05-02
> **Greblok said:**
> Tried to uninstall pysdm but as I later came to understand, this is just a GUI and the actual permissions are set elsewhere(?).


Indeed they are. They're in the file /etc/fstab. Can you post the contents of it here so we can see what pysdm has messed up?

---

### Post by Greblok on 2010-05-02
Thanks.
Here is the contens of the file:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc           proc  nodev,noexec,nosuid       0  0  
/host/ubuntu/disks/root.disk  /               ext4  loop,errors=remount-ro    0  1  
/host/ubuntu/disks/swap.disk  none            swap  loop,sw                   0  0  
/dev/fd0                      /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                     /media/sdb1     ntfs  defaults                  0  0  
/dev/sdc1                     /media/sdc1     ntfs  defaults                  0  0  I started to try different settings in pysdm but soon I realised this is to be done with caution,
hence, all is set back to default settings. :)

Among the things i tried was to allow any user to mount and unmount, and other things I thought could be relevant but with no luck.

Using 10.04LTS btw. _****_

---

### Post by Greblok on 2010-05-02
Ok, I think I solved it.

I had to edit the VB main program settings, where I had defined the actual disk as Default Harddisk folder and Default Machine folder.
The path was correct but it seems pysdm has changed some value which made VB not recognize the desired folder.
I just browsed to the correct folder for both settings again, and voila!

But, I still wonder why I can not mount and unmount the disk as i choose....

I am setting this thread as solved, but if any1 could enlighten me on the mounting issue, it would be greatly appreciated. :)

---

