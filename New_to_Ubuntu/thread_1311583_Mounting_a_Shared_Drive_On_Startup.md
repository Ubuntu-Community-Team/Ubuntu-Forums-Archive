---
title: "Mounting a Shared Drive On Startup"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Aurora@FleetBuzz on 2009-11-02
I just created a virtual machine in VirtualBox running Ubuntu 9.10 on a Windows XP host.  I created a directory for file sharing and it works but  I have to manually mount the drive each time I start Ubuntu.  Is there some way to edit a file so that this drive is automatically mounted?

The command I use to mount is:

> sudo mount -t vboxsf Don  /media/windows-share

Where Don is the folder name.

Could someone please provide the commands to permanently mount this folder?

---

### Post by TironN on 2009-11-02
Have you tried fstabbing it?

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

probably easiest

---

### Post by bodhi.zazen on 2009-11-02
> **Aurora@FleetBuzz said:**
> I just created a virtual machine in VirtualBox running Ubuntu 9.10 on a Windows XP host.  I created a directory for file sharing and it works but  I have to manually mount the drive each time I start Ubuntu.  Is there some way to edit a file so that this drive is automatically mounted?

The command I use to mount is:



Where Don is the folder name.

Could someone please provide the commands to permanently mount this folder?

You need to add an entry in fstab

>  /media/windows-share  Don  vboxsf  auto  0  0[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Aurora@FleetBuzz on 2009-11-02
Thanks for the quick replies!

I added to the end of fstab:
> /media/windows-share Don vboxsf auto 0 0 
but that didn't work.

However, when I again entered:
> sudo mount -t vboxsf Don  /media/windows-share
from the terminal, it worked!

Is the syntax right for the fstab entry?

---

### Post by bodhi.zazen on 2009-11-02
What is the name of you share ?

could be 

> Don  /media/windows-share  vboxsf  auto  0  0

---

### Post by Aurora@FleetBuzz on 2009-11-02
I access this via \file system\media\windows-share\Don

Should I list the entire path?

---

### Post by bodhi.zazen on 2009-11-02
[http://rotwhiler.wordpress.com/2008/10/09/mount-virtualbox-shared-folders-automatically-using-fstab/](http://rotwhiler.wordpress.com/2008/10/09/mount-virtualbox-shared-folders-automatically-using-fstab/)

---

### Post by Aurora@FleetBuzz on 2009-11-02
I tried your suggestion:

> Don /media/windows-share vboxsf auto 0 0 

That worked!

Thanks much.

Now I need to do this on a vista host; I may have to ask again!

---

