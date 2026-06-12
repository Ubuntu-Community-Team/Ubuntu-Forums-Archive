---
title: "Mounting SFS FS"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by xbar on 2008-12-11
I have a SATA drive that I want to mount on my new Ubuntu system.  
With fdisk, it identifies the drive as having a SFS file system.  After tinkering with directions given here: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive), and reading other forums, I was able to manually mount it by using this command:

 sudo mount -t ntfs-3g /dev/sda1 /media/Storage -o force

Not sure that that -o force command does, but it seems to have done the trick, and now my drive is mounted.  

Now, I want the drive to mount automatically at boot.  The typical 
  /dev/sda1    /media/Storage   ntfs-3g    defaults     0     2
doesn't seem to work.  Can you help?

Thanks in advance.

---

### Post by aheckler on 2008-12-11
Can't you just put "mount -t ntfs-3g /dev/sda1 /media/Storage -o force" in the Sessions startup list? That should work I think.

---

### Post by xbar on 2008-12-12
Thanks for the suggestion, but I'd rather not try unless it's a sure fix. 
Eg. the other line in fstab doesnt have the command "mount" in the line.




> **aheckler said:**
> Can't you just put "mount -t ntfs-3g /dev/sda1 /media/Storage -o force" in the Sessions startup list? That should work I think.

---

