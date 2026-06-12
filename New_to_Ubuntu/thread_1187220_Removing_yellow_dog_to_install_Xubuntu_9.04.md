---
title: "Removing yellow dog to install Xubuntu 9.04"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Windsurferdude on 2009-06-14
Hello, I just bought an iBook G4 from ebay that has yellow dog 6.1 installed. I have tried installing Xubuntu 9.04, but yellow dog will not allow me to access the disk. I have been able to live boot, but if I press the install icon nothing happens. I have spent a lot of time searching for a solution, but so far have been unsuccessful. Even running a search like "uinstall yellow dog" turns up nothing.  Thank you in advance. Scott

---

### Post by fooman on 2009-06-14
have you tried formatting the hard drive using the partition editor (gparted) on the live cd?

not sure on xubuntu...but on the ubuntu live cd,  it is under system > administration > partition editor

with the xubuntu live cd...have a look in applications > system > partition editor

when you find it....format the drive,  then try to install again.

hope that helps.

---

### Post by Windsurferdude on 2009-06-14
Hello, ok I managed to get into the partition program. What format should I use to repartition it?  Thanks

---

### Post by fooman on 2009-06-14
i would use ext3.

---

### Post by camper365 on 2009-06-14
ext4 is newer and will give you better performance however. I have used ext4 since Jaunty Alpha 6 (mid-March) and I have yet to have filesystem problems, other than not being able to use gfxboot (GRUB like in openSUSE). The only problems I am having are caused by me breaking different parts of the system. Right now I am running Karmic Alpha 2 so I am used to breakage.

---

### Post by camper365 on 2009-06-14
From the boot menu of the livecd have you tried selecting Install Xubuntu instead of Try Xubuntu without any change to your computer. The installer should come up and you can install it from there.

---

