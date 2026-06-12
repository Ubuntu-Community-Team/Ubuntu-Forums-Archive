---
title: "Boot hangs till 's' pressed."
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Bill Tomlinson on 2011-04-13
At one time, years ago, I had windows and two versions of ubuntu on my system. 

I added a more reliable drive and use it as my Ubuntu system drive.  I have eliminated windows and the older versions of Ubuntu.  

Now, with 10.10 (and formerly with 10.04) my boot stops at the Ubuntu splash screen  saying something like, "can not find Sdb5" and gives me the option of pressing the 's' key or doing a manual something or other.

I would like to get rid of this reference to that non-existent partition.   I am sure there are funny artifacts all over my system.  This does not really matter. I just want Ubuntu to boot fast and without extra key strokes.

---

### Post by jtarin on 2011-04-13
How many disk do you have? What is on your primary disk? What is on your secondary disk? Where is Grub located?

---

### Post by JKyleOKC on 2011-04-13
Post the content of your /etc/fstab file here so that we can see what partitions it says to mount automatically at boot time. You can open the file with a text editor, press ctrl-a to highlight all of it, then copy it to the clipboard. When replying, click the "#" icon on the toolbar of the reply dialog when you are ready to paste in the result, and then paste it (the cursor will be positioned between the code tags automatically). This will make it easily readable for us!

The odds are that this device is listed there, and simply removing it will solve your problem.

---

### Post by Bill Tomlinson on 2011-04-13
My drives are:     a western digital black   750 gig           sda
 
 partitions:          sda1      600 gig
                           sda5      12 gig swap
                           sda6      138 gig
I think this is my primary drive.  I chose it because of reliablilty.

            an old Seagate   320 gig                                        sdb
                                          
                            sdb1            

This was my old primary drive. I sometimes unplug it and use it on another machine.  It is not intended to be anything but storage now.


            a Seagate 1000 gig drive                                        sdc

  partitions:          sdc1    770 gig

                            sdc5    320 gig

I don't know where grub is.

---

### Post by Bill Tomlinson on 2011-04-13
[CODE][/CODE# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda6 during installation
UUID=5e579c5d-002d-454b-8487-e3bfbe0a0bc3  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=7ee48464-a850-404c-ac41-e364bb82ebd5  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdb5                                  /media/sdb5     ext4         defaults                  0  0  
/dev/sdb1                                  /media/sdb1     ext4         defaults                  0  0  
/dev/sdc5                                  /media/sdc5     ext4         defaults                  0  0  
/dev/sdc1                                  /media/sdc1     ext4         defaults                  0  0  ]> **JKyleOKC said:**
> Post the content of your /etc/fstab file here so that we can see what partitions it says to mount automatically at boot time. You can open the file with a text editor, press ctrl-a to highlight all of it, then copy it to the clipboard. When replying, click the "#" icon on the toolbar of the reply dialog when you are ready to paste in the result, and then paste it (the cursor will be positioned between the code tags automatically). This will make it easily readable for us!

The odds are that this device is listed there, and simply removing it will solve your problem.

---

### Post by bodhi.zazen on 2011-04-13
Open that file ```
gksu gedit /etc/fstab
``` and comment out the line with sdb5, by adding a # in front. 

```
#/dev/sdb5 /media/sdb5 ext4 defaults 0 0
```

Comment out any other partitions you do not always use.

Make the one you sometimes use "users,noauto" in the options column.

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by JKyleOKC on 2011-04-13
Okay, your fstab listing shows an entry for sdb5, but your earlier message shows only one partition now on sdb, so this is probably the culprit. Open /etc/fstab in a test editor, using sudo or gksudo to launch the editor with root privilege, and insert a "#" at the front of that line so that it looks like this:```
# /dev/sdb5 /media/sdb5 ext4 defaults 0 0 
```Then save the file, and you should be in good shape when you reboot. If that works, mark this thread as "solved" using the "Thread Tools" button at the top of the page...

---

### Post by Bill Tomlinson on 2011-04-13
You did it.   It works perfectly!!!!


> **JKyleOKC said:**
> Post the content of your /etc/fstab file here so that we can see what partitions it says to mount automatically at boot time. You can open the file with a text editor, press ctrl-a to highlight all of it, then copy it to the clipboard. When replying, click the "#" icon on the toolbar of the reply dialog when you are ready to paste in the result, and then paste it (the cursor will be positioned between the code tags automatically). This will make it easily readable for us!

The odds are that this device is listed there, and simply removing it will solve your problem.

---

### Post by Bill Tomlinson on 2011-04-13
```

```Thanks, you just describe the solution that worked.   Thanks to all who helped.   > **bodhi.zazen said:**
> Open that file ```
gksu gedit /etc/fstab
``` and comment out the line with sdb5, by adding a # in front. 

```
#/dev/sdb5 /media/sdb5 ext4 defaults 0 0
```Comment out any other partitions you do not always use.

Make the one you sometimes use "users,noauto" in the options column.

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

