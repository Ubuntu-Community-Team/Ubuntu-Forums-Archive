---
title: "Help with CD/DVD drive!"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by kiniyaloca1 on 2010-12-17
Hello, I am running maverick 64bit alongside windows7 on a partition. I cannot seem to find my cd-dvd drive. If i put a cd/dvd in nothing happens and my Cd-dvd drive does not appear in my "places tab" or in media folder... I am pretty new to linux.

Help much is apreciated

---

### Post by expatCM on 2010-12-17
So what you are saying is that the CD drive works with Windows 7?  If not, do you see the drive on the first page of the bios settings?

Could you please upload a copy of your fstab file?  (/etc/fstab)

---

### Post by kiniyaloca1 on 2010-12-17
Yes the drive works great with windows7. And i tried using the code you said (/etc/fstab), minus the "()" of course and nothing happened. Then i did ```
sudo gedit fstab 
``` and that brought up a blank text file...


Sorry, I found it. I suck with linux still...

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6b0fc5fd-505b-47b2-8560-6e8a497223f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7917b4f0-b027-4142-a43d-9fbc0fbe0e56 none            swap    sw              0       0

---

### Post by expatCM on 2010-12-17
and if you go to Places / Computer, do you see an icon for the drive in the window that opens?

I was expecting to see a line for the drive in fstab but it is not there.  However, I just looked at my own file and see it is not there as well so perhaps it is not needed with the current release.

---

### Post by kiniyaloca1 on 2010-12-17
No i dont see the drive there.

---

