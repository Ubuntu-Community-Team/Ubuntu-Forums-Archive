---
title: "Installed on USB,  fails on boot attempt."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by BFL DreamWorks on 2010-01-09
Cruzer Micro 2.0 USB thingy

EMachine 250-1162 with original N270 CPU, original 1gig ram,  250 gig HD/Win-7


Used the script on Pendrive Linux to make the bootable drive.   

Device boots to Menu and when I select the option to run from the drive it scrolls pages and pages of stuff, then it stops at the the line **"USBCORE:   *something something*  hiddev*"** then hangs.  


Also fails with same symptom when I select "check this install for errors" from the menu.

---

### Post by C.S.Cameron on 2010-01-09
I find the easiest way to make a bootable pendrive is to boot the Live CD and run System/Administration/Usb Startup Disk Creator.

---

### Post by danwosere2007 on 2010-01-09
Yo dude, i recently installed 9.10 nbr onto my netbook after failing once the first time. I did some research and then used the fdisk command to completely blank the usb stick and repartition it..i then formatted the usb into 2 seperate sectors using mkfs command (not sure if that was entirely neccescary to have 2 sections but there we go ;). I then used a program called unetbootin to install the operating system onto the empty usb stick. 
Installed straight away. Cant remember the code i used exactly but it was something along the lines of fdisk -l to find the device name (for me /dev/sdb1. i think i then did fdisk /dev/sdb1 as i recall. which brought up the partitioning part. Google or check the forums dude, i think i just followed some fairly easy instructions. Sorry i cant elaborate much further sorta beginner/intermediate so im probably not being much help =P, but repartitioning,formatting and then unetbooting seemed to work for me. Good luck dude! - Dan

---

### Post by BFL DreamWorks on 2010-01-09
Two other people gave me the same advice.

Apparently this SANDISC MICRO has two logical devices on it...  one is the USB Drive proper the other is the the SanDisc operating system and it looks/acts like a CDROM drive.   Apparently Linux thinks it is finding a CDROM drive as it is assembling itself.

So somehow I have to nuke that other logical device off of here and try again.

---

### Post by danwosere2007 on 2010-01-09
I was using hardy heron myself so i couldnt go the liveusb route sadly and had to do things old skool. 
Heres what i did if i can recall correctly and it helps at all...

Firstly i erased all data on the usb stick manually...

sudo fdisk -l

 this lists devices on your computer...i then looked for the usb which was the 2gb sorta size it was /dev/sdb1 on my computer. 

i think i then ran sudo fdisk /dev/sdb1

which brought up a partitioning program...

i typed d 1 and 2 to delete the partitions allready on there..

 i typed n to create new partion p to make it primary and 1 to make it the first one... then set 1 as the first sector +800M to make it 800mb large and then t to set the type of partition. i believe i chose either 6 or b for fat16 or fat32 respectively. This is all bad recollections though there was a very extensive guide that i used upon typing formatting usb stick...which ive just found for you...

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

yupo rather than listen to me ramble on about how i might of done it, check this page out. It helped me out a ton. I then just did the unetbootin thing and boom baby i was in business.

Hope this helps...

Good luck 

-Dan

(Edit* upon reading that page i realised that i completely neglected the unmounting of the disk first, just check out the link rather than following my dumb instructions haha ;)

---

### Post by BFL DreamWorks on 2010-01-09
Thank you for the advice, but how do I do this under Windows Seven.    I can't touch that other partition/logical device with what I have.

---

### Post by C.S.Cameron on 2010-01-10
You should be able to make a gparted Live USB using unetbootin.
Parted Magic is listed under Distribution in Unetbootin

---

