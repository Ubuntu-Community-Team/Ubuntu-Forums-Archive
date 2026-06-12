---
title: "Full Install to USB"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-11-16
I've been researching this topic lately and I realized that finding an ideal USB distro would be great for my school computer usage as the combined proxy and lack of decent programs at my school is unbearable. I realize that Ubuntu can install to a flash drive but 1) I'm not too sure how to do it correctly and 2) I'm not too sure what distro would be able to fit and work well on a 4gb flash drive. I'm not worried about wear and tear so instructions can be as basic as possible.

Thanks

---

### Post by SPazzo on 2009-11-16
Try using [Unetbootin]("http://unetbootin.sourceforge.net/").  It was made for people who don't have a disc drive (i.e. netbook users), but it'll work for your cause too.

---

### Post by Martin Marshalek on 2009-11-16
My problem is is that Unetbootin only makes Live ISO's. That's great but then I can't save changes. I'm pretty sure that for some distributions (like Ubuntu) you can install from the liveCD using the regular installer to install to the flash drive but, since my drive isn't one of those 64gb 1000000000000000000 mb/s drives, regular Ubuntu might not be the best choice.

---

### Post by Matt Yun on 2009-11-16
This website has tons of info on USB-based distros: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

On my 16GB flash drive, I have Slax, Tinycore and Pubuntu (a coLinux based Ubuntu that runs in Windows).

---

### Post by Dude-PWB- on 2009-11-16
I just used the usb startup disc option in system > Administration and walked through it, and it asks you if you want to use the rest of the free space for your settings, and it works nicely.

Saves everything I do, but it does boot like a livecd. Stilld does updates and whatnot, works real well.

---

### Post by alexfish on 2009-11-16
when ubuntu 8.04 came out it ran fine on a 4gb usb stick as full install.
updates and every thing work flawless  later distros dont work on usb sticks on full install
but can work as a live cd with a home folder or a loop file. ubuntu 9.04 has usb start up disk creator and works fine /  for full installs i prefer usb hard drive . they are now at a fair price for storage per mbyte/  and will last longer than a usb stick 

before full installs on external drives look for threads on how to / avoid grub
installing on your existing internal hard drives

added
you also need to check if the bios can boot from a usb device

---

### Post by Johnny2good on 2009-11-19
I installed debian lenny on a external hard drive much the same setup worked first boot after install ;) you will find help on the link.. i used [Unetbootin]("http://unetbootin.sourceforge.net/").


[http://blogs.koolwal.net/2009/01/28/installing-linux-on-usb-part-2-install-debian-lenny-on-usb-hard-drive/](http://blogs.koolwal.net/2009/01/28/installing-linux-on-usb-part-2-install-debian-lenny-on-usb-hard-drive/)

---

### Post by sgosnell on 2009-11-19
Unetbootin makes live CD distros, which you then use to install to another USB drive.  You'll need a drive bigger than 4GB to get much functionality, although it's possible to put Ubuntu on one that size.  USB drives are pretty cheap, so I would suggest an 8 or even 16GB drive.  You'll need another drive to install to, anyway.  1GB is big enough for the live CD install.

---

