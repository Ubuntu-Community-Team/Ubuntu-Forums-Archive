---
title: "Cannot Boot without my USB Drive connected"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by waYYne on 2010-05-24
HI All, 

i made the mistake of installing Ubuntu whilst having my portable USB drive connected. Now if i restart my machine with that drive unplugged i get a grub error.  

Is there anything i can do to make it boot with this drive unatached (its not a system disk)

thanks in advance

---

### Post by ankspo71 on 2010-05-24
Hi,
Here is information on changing the location of the grub:
[Changing or Moving GRUB 2]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")
Hope that helps.

---

### Post by ajgreeny on 2010-05-24
What ankspo71 didn't say is that you need to put grub onto the USB disk and restore whatever boot manager you had on the internal disk.  If you have windows on that you will need to reinstall the windows MBR, and how you do that depends on the version of windows.  Now set the USB as forst bootmdevice and the internal disk as second.   Then if the USB disk is attached, grub will take over the boot and give you the choice of OS to use, if the USB disk is not attached, the system will go to the hard disk for the boot manager.

A google search should find out how to do the windows MBR bit quickly.

---

