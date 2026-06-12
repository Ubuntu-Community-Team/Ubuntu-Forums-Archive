---
title: "No media in drive (USB pen drive)"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Lancer074 on 2010-05-15
Hello.  I am somewhat new to linux.  I had a 8gig flash drive in the computer and it was mounted in Ubuntu fine.  However, being the noob I am, I just jerked the drive out without thinking and now it will not mount again.  It shows up as USB drive in "places", but will not mount.  I tried to force the mount to /media/usb and it said "unknown device".

If I open gparted, it is not listed under devices at all.  Just my hdd is there.

Also, I tried plugging it into a windows machine, it shows up as a removable media, but will not open.  I have tried formatting it in windows with several tools to no avail.

Any help would be great, I would hate to find out that I so easily turned my flash drive into a paper weight. 

Thanks in advance.

---

### Post by -humanaut- on 2010-05-15
Plug it in instead of forcing it to mount you'll need to force it to unmount. What happen was when you pulled it out without unmounting it properly it locked the device. Format it with Gparted and restart your computer with the device plugged in. That should mount it then you can unmount and it should work fine.

---

### Post by trentscott on 2010-05-15
> **-humanaut- said:**
> Plug it in instead of forcing it to mount you'll need to force it to unmount. What happen was when you pulled it out without unmounting it properly it locked the device. Format it with Gparted and restart your computer with the device plugged in. That should mount it then you can unmount and it should work fine.

+1 I've run into issues when I format a drive with gParted and try to open it up in terminal. The solution is to do what you need in gParted and remove + reinsert the drive when it finishes. You could also reboot...

---

### Post by Lancer074 on 2010-05-15
Ok, I tried 

umount /dev/sdb
             


it says  device not mounted.

I also tried umount /dev/sdb1 and it says the same thing.

Feel free to correct the way I was trying to unmount, I only somewhat know what I'm doing.

---

### Post by -humanaut- on 2010-05-15
Use Gparted to format the drive to fat32 and reboot the computer with the drive still inserted.

---

### Post by Lancer074 on 2010-05-15
Gparted only shows my hdd as a device.  My usb drive does not show up in gparted at all, therefore, I do not know how to use gparted to format it. 

Thank you all for your replies thus far, sorry that it so far has not fixed anything.

---

### Post by -humanaut- on 2010-05-15
Have you plugged in the USB device and tried rebooting the Computer with the device plugged in?

---

### Post by garvinrick4 on 2010-05-16
In gparted click drop down menu in gparted drop down menu and click devices. Your flash drive should be there. Open that drive, when is on screen right click on device and find format and choose fat32 then go to Apply check mark up top and apply it and you will be reformatted. Now right click again and go to Label and type in a Label (lets say flash for this) now click on the apply arrow again and you have a label on the device. Now if it will not mount you can use this. And later on you will need this.


```
sudo mount /dev/sdb1 /media/flash
```sudo=super user
Mount=mount
/dev/sdb1 = the device and the partition #
/media/flash= the label of the device

To Unmount:

```
sudo umount /media/flash
```That is not a typo umount is correct for unmounting.
Always unmount using code when you mount using code.

You can mount any partition in your 

```
fdisk -l  
```That is a small L.

Give all your partitions a Label it will be easier.
You can see them by. Always use this to make sure of your partition or device #'s  sda1, sda5, sdb1 and such.

```
sudo blkid
```

---

### Post by nice1stu on 2011-03-09
Not sure if you have  solved this problem, but this is a common problem and not restricted to Ubuntu. I was trying to create a usb boot stick with jolicloud live cd when error occured and the exact same problem occured with my flash stick. Probably the file allocation table got corrupted. (Did so when I pulled the stick when it had crashed I guess. Couldn't safely remove since it had crashed)
 
Have a look at this link, it offers multiple solutions depending on the brand of your stick, or finally if all else fails use the windows installation disk to format the stick.
 
[http://www.ardamis.com/2009/07/02/usb-drive-unusable-unformattable-and-reporting-0-bytes-capacity/](http://www.ardamis.com/2009/07/02/usb-drive-unusable-unformattable-and-reporting-0-bytes-capacity/)

unfortunately none of the solutions worked for my usb stick, but I keep trying

---

