---
title: "multiple usb drives keeping them straight"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by I_M_smbody on 2009-04-22
I have more that one usb drive  attached to my server each one serves a different purpose and has different data. How do I keep them straight in linux so if I unplug them  and then plug them in a different order the device names don't get screwed up? for instance i don't want /dev/sde video  drive  being confused with /dev/sdf the documents drive. can I predetermine what device name will be assigned to each drive? it would be nice to be able to put them in fstab.


Thanks

I_m_smbody

---

### Post by bodhi.zazen on 2009-04-22
put an entry in fstab for each device, either by UUID or label.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by mgmiller on 2009-04-22
USB drives should not be mounted in fstab.  Since they are removables, they automount when plugged in/powered on.

Turn on the drive and then run gparted ( System > Administration > Partition Editor.  

Use the drop down on the right side to display the USB drive in question.  Next you will right click it in gparted and tell it to unmount.  

You can then right click it and choose the option "Label"  Type in what you want and click apply.

You will then need to unplug and replug the drive and it should automount with the new name displayed.

Like anything else, when you are messing with drives like this, make sure everything on it is backed up first.

---

### Post by bodhi.zazen on 2009-04-22
Well, he did say server, so I assume he does not have gnome on the server.

fstab is also the way to go if you do not want your drives to be mounted in /media ;)

so, just to clarify, there is nothing "wrong" with using fstab.

I do not think gparted is installed by default , so you may need to ```
sudo apt-get install gparted
```

Otherwise, yes, setting a label on a drive is the way to go and this is what I do on a desktop.

---

### Post by steve101101 on 2009-04-22
> **bodhi.zazen said:**
> well, he did say server, so i assume he does not have gnome on the server.

Fstab is also the way to go if you do not want your drives to be mounted in /media ;)

so, just to clarify, there is nothing "wrong" with using fstab.

I do not think gparted is installed by default , so you may need to ```
sudo apt-get install gparted
```

otherwise, yes, setting a label on a drive is the way to go and this is what i do on a desktop.

+1

---

### Post by I_M_smbody on 2009-04-23
Hi guys

Thanks for the replies
It is a server machine with no gui so gparted won't work for me this time but I'll keep it in mind for the desktop.

I've been reading the material on fstab with a label and uuid and that seems to be the way to go.
 
I install the drives and it shows up both from dmesg and fdisk -l. I can manually mount the drives and dismount them before removing the drive. 

Is there any way to check if the drive is in use before I unmount it so I don't accidentally corrupt files if someone else on the network is using it?

Ideally I'd like to have it mount automatically when it is inserted and have it check to see if it is not in use before dismounting for removal( if I can figure  out the manual commands  I can probably write a dismount script).

Thanks again for your help

I_M_smbody

---

### Post by bodhi.zazen on 2009-04-23
[uhelp]Mount/USB[/uhelp] suggests you try a package "usbmount"

I have not tried it ;)

Usually if the device is in use you can not unmount it.

If you want to check, try lsof , grep for the device name / mount point.

```
sudo lsof | grep /mount/point
```

You could likely write a wrapper script ;)

---

