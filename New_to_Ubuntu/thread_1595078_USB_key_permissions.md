---
title: "USB key permissions"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-10-12
Hi all. 

I have a few questions about fstab and usb key permissions.

It seems that over time that my mounted drives have been accruing errors- when I view my /media folder, my drives have extra underscores appended to their titles. For example, my Toshiba external drive is listed as TOSHIBA__ with 2 underscores. A TOSHIBA_ and TOSHIBA are both listed there too. 


What happened to cause this?


Also, on a related note, I had a usb key that i would back my /home folder up to (using sudo permissions) and now it seems that the drive is stuck with its owner set as root, even on other computers. Whats the proper way to reset this? I already tried to reformat the drive several times.


Thanks for the help!

---

### Post by JustinR on 2010-10-12
> **tom.swartz07 said:**
> Hi all. 

I have a few questions about fstab and usb key permissions.

It seems that over time that my mounted drives have been accruing errors- when I view my /media folder, my drives have extra underscores appended to their titles. For example, my Toshiba external drive is listed as TOSHIBA__ with 2 underscores. A TOSHIBA_ and TOSHIBA are both listed there too. 


What happened to cause this?


Also, on a related note, I had a usb key that i would back my /home folder up to (using sudo permissions) and now it seems that the drive is stuck with its owner set as root, even on other computers. Whats the proper way to reset this? I already tried to reformat the drive several times.


Thanks for the help!

Hi, when Ubuntu mounts drives, sometimes it doesn't delete the folder it created in /mount, resulting in new folders with the same name with '_' added. Once the drive is removed, you can use the terminal or 'gksudo nautilus /media' to delete the redundant folders.

If your using a Linux file system on your USB flash drive, it has its own set of permissions - and on other computers this appears as Root - because the username you created on your computer isn't on another computer. You can reformat the drive in something like 'Disk Utility' and when you select the filesystem, if it's a linux one, unclick the box that says 'Take Ownership of Filesystem'.

---

### Post by garvinrick4 on 2010-10-12
> **tom.swartz07 said:**
> Hi all. 

I have a few questions about fstab and usb key permissions.

It seems that over time that my mounted drives have been accruing errors- when I view my /media folder, my drives have extra underscores appended to their titles. For example, my Toshiba external drive is listed as TOSHIBA__ with 2 underscores. A TOSHIBA_ and TOSHIBA are both listed there too. 


What happened to cause this?


Also, on a related note, I had a usb key that i would back my /home folder up to (using sudo permissions) and now it seems that the drive is stuck with its owner set as root, even on other computers. Whats the proper way to reset this? I already tried to reformat the drive several times.


Thanks for the help!Open media in Root and toss them,
Alt/F2 type in gksudo nautilus file sytem to Media open and delete them all. It will make one when mounted and delete when unmounted do not need them. 
 What do you format the flash drive in Fat32, ntfs, ext?

---

### Post by tom.swartz07 on 2010-10-12
> **garvinrick4 said:**
> Open media in Root and toss them,
Alt/F2 type in gksudo nautilus file sytem to Media open and delete them all. It will make one when mounted and delete when unmounted do not need them. 
 What do you format the flash drive in Fat32, ntfs, ext?

I figured I could just throw the old folders, but I wasnt sure.


I have the usb formatted as ext4, and even when unchecking the 'take ownership' box, it still will not let me write to it.

---

### Post by tom.swartz07 on 2010-10-12
WAIT!

Scratch that- when I CHECK the box that says 'take ownership' it allows me to write to it.


PERFECT!



Everythings good now. Thanks for the info about using the Disk Utility to format it in that way.

/thread

---

