---
title: "Sucessfully installed Ubuntu dual boot XP, GRUB"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by admaw11 on 2010-12-09
The main problem was I was too scared to let the Ubuntu installer install the boot loader - thinking it would alter the MBR then not be able to boot. (this meant after installation linux would not boot off the drive, just blank screen and blinking cursor - due to Grub not being installed)
But I found it allows the installation of GRUB onto just the partition where Ubuntu is, so when I select to boot off the Ubuntu partition (via my other boot loader) Grub comes up then, and can sucessfully boot ubuntu.
So does this mean Grub has not actually altered the MBR of the drive at all? 
XP has been completely uneffected by all this thankfully.

The next challenge is to get SLAX linux onto the boot menu(s) without stuffing up the MBR (slax came with a script that updates the MBR - not sure if that means it will replace it completely, or just its own partition or just add a menu option etc)

cheers,

Adam.

---

### Post by oldfred on 2010-12-10
If you are installing more than one system, you should learn to read this boot info script and run it before & after each change to partitions or systems. I also run it as part of my backup script, so I have a detailed list of partitions and what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

