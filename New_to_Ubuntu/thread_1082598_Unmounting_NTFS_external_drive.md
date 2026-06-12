---
title: "Unmounting NTFS external drive"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by aihre on 2009-02-27
Hello everyone,

I have an NTFS-formatted external HDD that I use for storage.  I'm able to mount it without problems.  However, when I unmount it by right-clicking on the Desktop icon and selecting "Eject Volume", the HDD unmounts and the icon disappears momentarily, but then immediately returns and remounts (and the folder automatically opens).  I've tried ejecting it from the Desktop repeatedly without success: the drive keeps remounting.

I've also tried unmounting the drive via Terminal...
```
sudo umount /dev/sdb1/
```

...and the drive disappears from the /media folder.  But the icon doesn't disappear from Desktop, and the drive remounts when I click on the icon.

Can someone tell me what's going on, and how this can be fixed?
If the HDD disappears from /media, is it OK to turn it off even if the icon remains on the Desktop?

Thanks in advance!

---

### Post by Ms_Angel_D on 2009-02-28
Try using Unmount instead of eject, it's in the same right-click menu.

---

### Post by aihre on 2009-02-28
> **MetalHellsAngel said:**
> Try using Unmount instead of eject, it's in the same right-click menu.

I'm afraid there's no such entry in the right-click menu.  If it helps, I'm using Xubuntu.

---

### Post by adult swim on 2009-02-28
unmount the drive, then go to a terminal and run ```
mount
``` to see if it is mounted

---

### Post by rhcm123 on 2009-02-28
It might (actually, probably) be mounted via hal, which likes to automount drives like that, annoying and repeatedly, or it could be the auto switch malfuntioning in your fstab.

Please post your /etc/fstab file and then try the following: 
Add the "disk mounter" applet to main panel.
Click on disk. Select unmount.

Edit: Your unmounting the wrong thing -you are unmounting the drive instead of the mount point. If your drive is /media/foobar
then run the following:
```
sudo umount /media/foobar
```

---

### Post by aihre on 2009-02-28
Thanks everyone,

So the HDD is /dev/sdb1 and /media/WINTERMUTE (that's its name :) )

I tried unmounting the drive via **sudo umount /media/WINTERMUTE** and **mount** shows that it's gone, but the icon persists in the Desktop and in file manager.

The drive isn't in /etc/fstab either even when mounted (it shows up in **mount** though):
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=50e1615e-14e0-421e-94af-d9c5e5bca4b1 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=ec49ecae-8b99-419e-851e-ee7ec5fb0585 /home           ext3    relatime      
  0       2
# /dev/sda2
UUID=52c01828-1bc8-493f-a626-8b79b98c61ec none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


I think **mount** is showing that the HDD is unmounted.  But the icons on the Desktop persist.  I want the Desktop to reflect what I see in Terminal.

I also added the applet that rhcm123 was talking about (it's called Mount Devices), but somehow I can't seem to unmount drives from there.  (No right/left click menu...)

Can help?

---

### Post by rhcm123 on 2009-02-28
> **aihre said:**
> Thanks everyone,

So the HDD is /dev/sdb1 and /media/WINTERMUTE (that's its name :) )

I tried unmounting the drive via **sudo umount /media/WINTERMUTE** and **mount** shows that it's gone, but the icon persists in the Desktop and in file manager.

The drive isn't in /etc/fstab either even when mounted (it shows up in **mount** though): (rhcm123 cut this out to make the output shorter :))

I think **mount** is showing that the HDD is unmounted.  But the icons on the Desktop persist.  I want the Desktop to reflect what I see in Terminal.

I also added the applet that rhcm123 was talking about (it's called Mount Devices), but somehow I can't seem to unmount drives from there.  (No right/left click menu...)

Can help?

Alright, the applet dosen't work? That's odd, it's one of my favorites and i've found it very reliable. But thats another problem, and we'll work on that later.

After you umounted /media/WINTERMUTE go back to the icons and click on them. If you get a message "cannot open WINDERMUTE.volume, there is no application installed for this file type" then these are merely the HAL/nautilus icons sticking and this can be dealt with. (This happens to me all the time when i unplug my USB NTFS-formatted HDD.) 

If not, then it is (for some reason) still mounted somewhere, which is a much bigger pain in the butt.

---

### Post by aihre on 2009-03-01
> **rhcm123 said:**
> After you umounted /media/WINTERMUTE go back to the icons and click on them. If you get a message "cannot open WINDERMUTE.volume, there is no application installed for this file type" then these are merely the HAL/nautilus icons sticking and this can be dealt with. (This happens to me all the time when i unplug my USB NTFS-formatted HDD.) 

If not, then it is (for some reason) still mounted somewhere, which is a much bigger pain in the butt.

@rhcm123:
Yes, WINTERMUTE still mounts, even after unmounting it via Terminal.

---

### Post by rhcm123 on 2009-03-02
> **aihre said:**
> @rhcm123:
Yes, WINTERMUTE still mounts, even after unmounting it via Terminal.

ok, try this: Unmount it, then unplug it :) It sounds simple, because it probably is. User puts in request for drive, HAL sees drive not mounted, mounts drive for user. If, after you unplug it, the icon is still there, i can teach you how to kill that.

---

### Post by aihre on 2009-03-04
> **rhcm123 said:**
> ok, try this: Unmount it, then unplug it :) It sounds simple, because it probably is. User puts in request for drive, HAL sees drive not mounted, mounts drive for user. If, after you unplug it, the icon is still there, i can teach you how to kill that.

Thanks for sticking it out with me - sorry for the delays in replies!

If it's okay to unplug my HDD even after I've unmounted it via command line, I'm okay with having the icon stick around, even though it's annoying.  I just don't want to mess things up by unplugging drives when I shouldn't be... :)

I also noticed that when I plugged in another drive (my MP3 player, formatted as vfat) and eject it by right-clicking the Desktop icon, it works fine and the icon disappears.  So it may just be my NTFS-formatted HDD that's the problem here...

---

### Post by abhishek.malhotra35 on 2009-03-04
I don't think NTFS formatted HDD should be an issue. I am also using HDD with NTFS format. Does your hard drive gives a mount error when you plug it in after removing.

---

### Post by abhishek.malhotra35 on 2009-03-04
Also check that your automount is off. I found an article on how to disable automount. [http://ubuntuforums.org/showthread.php?t=13692](http://ubuntuforums.org/showthread.php?t=13692). Hope this might help you.

---

