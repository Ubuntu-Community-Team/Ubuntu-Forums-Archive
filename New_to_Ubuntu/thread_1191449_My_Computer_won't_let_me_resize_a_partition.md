---
title: "My Computer won't let me resize a partition"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Travis_A on 2009-06-19
I have finally got online with Ubuntu after picking up a RetailPlus USB wireless receiver, and Ubuntu put up a list of updates for me to install. When I tried to install them however I received a message that said:

> Not enough free disk space

The upgrade needs a total of 367M free space on disk '/'. Please free at least an additional 367M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.So my first idea was to beef up my Ubuntu partition. I had originally made a "Linux" partition in Windows to install Ubuntu on, but not really knowing how to configure the setup I let Ubuntu make its own partition (about 2.5 GB). It was this partition that I deleted in Windows Vista's disk management that I was going to use to add to the Ubuntu partition. However after deleting the volume I am now left with a 14.88 GB block of unallocated space that both Windows disk management and GParted seem to refuse to let me add to an existing partition. They allow me to make a new partition out of the space, but nothing else.

Does anybody have any idea why I can't use my unallocated disk space to extend my Ubuntu partition? I have been trying to figure this out for some time now and it is becoming very frustrating.

---

### Post by snakeman21 on 2009-06-19
You can't resize a partition on a disk that is in use.  The only way to resize partitions on your hard drive is to boot from an external media.  The best way to do this is by booting from either an Ubuntu live CD or live USB.  Then, go to system > administration > partition editor and edit the partition from there.  Good luck!

---

### Post by lindsay7 on 2009-06-19
Go to the Gparted web site and download this program and burn it to a disk.  It will then be bootable and when you boot it the drives on your computer will be unmounted and can be worked on as you like.  There is also great documentation on their site for using this application.

---

### Post by snakeman21 on 2009-06-19
> **lindsay7 said:**
> Go to the Gparted web site and download this program and burn it to a disk.  It will then be bootable and when you boot it the drives on your computer will be unmounted and can be worked on as you like.  There is also great documentation on their site for using this application.

That will work just as well, yes.  I just figured that booting with a familiar GUI would be easier :P

---

### Post by lindsay7 on 2009-06-19
I like a couple of things that the Gparted live cd has to offer,

1. the system drives are unmounted automatically
2. there is a screen shot tool in the Gparted menu, great if the user needs help.

3. it loads very fast.
4. it is just a good tool to have around

---

### Post by snakeman21 on 2009-06-19
Agreed.  I actually keep two USB sticks on my keychain.  One has a Jaunty persistent install that I use for recovering files from broken systems that won't boot (usually windows systems), and one with a bootable gparted.  I use the Jaunty live USB much more often, but gparted IS a wonderful little tool to have handy.

---

### Post by lindsay7 on 2009-06-19
Snakeman,

That is a great idea, it kind of makes you a walking repair kit. A Supergrub usb would have it all covered for the most part.  I just made a dvd with the "System Rescue" programs. Check it out here.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

