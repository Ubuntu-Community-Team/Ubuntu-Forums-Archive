---
title: "detects digital cam with usb but wont open"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by echo8172 on 2009-03-04
Yah guys just a cheapo 30 dollar camera (aries), and I downloaded the software with  wine and it wont open also tried opening with other programs just wont detect the camera but I believe it is detecting it right?
   Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0979:0227 Jeilin Technology Corp., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04b3:310c IBM Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 07b2:5120 Motorola BCS, Inc. SurfBoard SB5120 Cable Modem (RNDIS)
Bus 001 Device 004: ID 046d:c30b Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
admin@admin-desktop:~$ 
    I believe the jeilin is the camera right?..If anyone knows the info would help thank u

---

### Post by ajgreeny on 2009-03-04
Does the camera show on the desktop when you plug it in to the computer (with USB?).  If it does just double click on that icon and it should open nautilus to show you the pictures on the camera.

However, perhaps it's not quite that simple.  So with the camera plugged in, try ```
sudo fdisk -l
``` in terminal and post the output here.  Also look in /media to see if there is a new folder made automatically for the camera.

---

### Post by echo8172 on 2009-03-05
Thanks for the reply..there is no camera showing on the desktop but I did do the following....
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris
admin@admin-desktop:~$ /media
bash: /media: is a directory
admin@admin-desktop:~$ 


    Probably if there is no solution to this Im just going to save my money for a better camera that linux will reconize

---

### Post by ajgreeny on 2009-03-05
To see what is in /media the command should be ```
ls -l /media
```not just ```
/media
```

---

### Post by Gawains Green Knight on 2009-12-14
I have the same camera (aries 3 in 1 digital camera sold exclusively at Walgreens). gphoto2 and digikam couldn't auto detect and nothing in /media or on desktop (at least running xubuntu 9.04). That pretty much exhausts my knowledge of digital camera detection.... the camera says that it stores images in an uncompressed format so I had hoped it would work. For $20 it was worth a shot though.

---

### Post by anewguy on 2009-12-14
I really don't think it will help, as I believe the camera uses specialized drivers, but try running one of the photo programs as root.  *IF* that works, then it's a permissions problem we can work around (this particular type won't say you don't have permissions, the camera just won't show to the program).

If it does use specialized drivers as I suspect, then it becomes next to impossible.  I have a program that works with cameras from CVS and Rite-Aid, but they are based on Pure Digital and sMal technologies, so I doubt it would work with your camera.

I'll do some additional searching and post back if I find anything else.

Dave :)

---

### Post by llamabr on 2009-12-14
wine is very rarely the correct solution.

Plus in the camera, hang back 15 seconds or so, then post:

```
dmesg | tail
```

and 

```
df
```

---

### Post by mikechant on 2009-12-15
Some cameras have mode settings in the camera menus. For example mine allows you to switch between MSS (normal mass storage mode) and PTP (Photo Transfer Protocol). In my case PTP mode works with Ubuntu but MSS mode doesn't.

---

### Post by Gawains Green Knight on 2009-12-15
Thanks for the ideas! 

Yeah, the camera isn't mounting at all.... its like its not even there. Although the previous post mentioned that it was detected?

I was wondering if ndiswrapper might help as I have the windows drivers?

The camera his limited options concerning resolution and compression of images, but nothing useful.

EDIT: 

[176020.736577] usb 2-7: USB disconnect, address 7
[176036.428039] usb 2-7: new full speed USB device using ohci_hcd and address 8
[176036.641227] usb 2-7: configuration #1 chosen from 1 choice
[176036.824550] usb 2-7: reset full speed USB device using ohci_hcd and address 8

just came up after dmesg | tail

and 

Bus 002 Device 007: ID 0979:0227 Jeilin Technology Corp., Ltd 

after lsusb.

So it at least exists! No sdb's or anything camera like in df.

---

### Post by ukripper on 2009-12-15
can you reconnect your camera and post output of this command as other poster requested above:
```
dmesg | tail
```

---

### Post by soldier4jesus on 2009-12-15
Does the camera have a memory card in it?  The reason I'm asking is, I couldn't get my Kodak digital camera to mount correctly on my computer when I plugged it into one of the USB ports. So, what I did was, I took the memory card out and put it in one of the media slots that's on the front of my computer and it does fine that way.  It will show the memory card up on the desktop and will transfer all of my pictures to F-spot.  When I'm finished, I can then unmount it and take the card out.  I hope this helps.

God Bless!!
Wesley

---

### Post by Gawains Green Knight on 2009-12-15
Thanks for the help and feedback. I found a number of posts concerning these cameras on other forums - with no solution. Apparently the data is encrypted or compressed in some way that is a pain. Anyway, I plugged it into a windows machine to see if it would work and the quality of the picture really doesn't justify the morning wasted trying to get this thing to work on linux. Its as good as a low end camera on a phone. Although I didn't expect much and its good enough for my needs (grainy bw pictures of physics lab equipment). Thanks again!

---

### Post by anewguy on 2009-12-15
I found a single post about someone working on a driver, but that was from a while ago, and they never got it working.

Dave :)

---

### Post by Gawains Green Knight on 2009-12-16
My next bet would have been trying wine - apparently it can handle usb

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

not entirely clear if it can only handle devices already detectable in linux, or if it can be used to handle windows drivers. 

I guess I'll have to vote with my dollar and only buy stuff that is linux-friendly!

---

