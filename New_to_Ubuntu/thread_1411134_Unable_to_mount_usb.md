---
title: "Unable to mount usb"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by degarb on 2010-02-19
Jesus, this file system sucks.

Firstly, I cannot see how much room is on my usb stick in nautist, no properties STANDARD RIGHT CLICK MENU.  Then, I unmount, but I don't see a way to remount.   Googling give me code.  But I don't know how to find out the sda0 from sda1`  from sdb0  etc.  Plus again, only a 1988 OS would require a command line to mount (certainly not one that cares about how many programs are written for it), so I must be missing something. 

Now, I am 40, so talk/write slowly.  Heck, I could never get the UNIX file system when I hit 30. 


How do I mount.  And where again are my hard drives in the file system. Back again to the manual and diagram.

---

### Post by Temposs on 2010-02-19
If you're running the standard Ubuntu 9.10, most usb flash drives should mount automatically. I haven't really seen any that don't. The fact that you say you're unmounting tells me that your usb flash drive is in fact mounting.

If you want to see a lot of info about your hard disks, go to System->Administration->Disk Utility. Lots of info there :-)

Also, it's easy to see the free space on a drive in Nautilus. Usually, whenever you're in nautilus, if you look at the bottom of the window, it will say how many items are in your current directory and then how much free space is on the disk that you're currently looking at. You can also get this information in Nautilus by right-clicking on a blank area in Nautilus and choosing Properties.

---

### Post by degarb on 2010-02-19
Thanks.


I unplugged and replugged stick.   I didn't see it show up in nautilist.   I went away and did other stuff.   Then came back and tried entering this time through places.   Clicked mem stick and see it now mounted.




How do I format it with linux ext4?

---

### Post by Temposs on 2010-02-19
> **degarb said:**
> Thanks.


I unplugged and replugged stick.   I didn't see it show up in nautilist.   I went away and did other stuff.   Then came back and tried entering this time through places.   Clicked mem stick and see it now mounted.




How do I format it with linux ext4?

Good job!

You can format a drive with the gparted(GNOME Partition Editor) program, which you can get from the Ubuntu Software Center. Just search for it and install :-)

---

### Post by degarb on 2010-02-19
> **Temposs said:**
> Good job!

You can format a drive with the gparted(GNOME Partition Editor) program, which you can get from the Ubuntu Software Center. Just search for it and install :-)


Thanks, I will download it.   

I did it by: 
mount  to find voodoo (to me) 5 drive lettering system. then,
sudo umount /dev/sdb1
sudo mkfs -t vfat /dev/sdb1  ; some memorization here that will preclude using this in future
sudo eject /dev/sdb1


I hope nautilist will do formatting in futue,  cause a year from now, I won't remember this program name--I will be one more year older and more feeble minded.  So, if on another system, something that should take 30 seconds will take 10 minutes to research and download.

---

