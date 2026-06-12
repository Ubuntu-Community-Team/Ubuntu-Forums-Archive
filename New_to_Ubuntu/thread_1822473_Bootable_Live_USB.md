---
title: "Bootable Live USB"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by avnd on 2011-08-10
Hello!

I wanted to try Ophcrack. So I downloaded the Live CD .iso from [http://ophcrack.sourceforge.net/]("http://ophcrack.sourceforge.net/")

Now I want to create a bootable USB with this .iso. I tried the manual option suggested at [http://sourceforge.net/apps/mediawiki/ophcrack/index.php?title=Frequently_Asked_Questions#How_to_installl_the_LiveCD_on_a_USB_stick.3F]("http://sourceforge.net/apps/mediawiki/ophcrack/index.php?title=Frequently_Asked_Questions#How_to_installl_the_LiveCD_on_a_USB_stick.3F")

I had no hitches while doing that, but my Compaq Presario C751NR doesn't boot from it. It detects the USB drive in the boot menu option but just gives a blank black screen with a cursor when I boot from it. 

To make sure, the .iso wasn't faulty (I did check the md5sum. It was okay) I burned the image on to a CD and that CD boots fine.

I then tried another method. The 'dd if= of=' method from the terminal. Again, all the relevant folders were present in the USB key but the PC doesn't boot from the key. 

Now since the .iso is basically a linux based OS (correct me if I'm wrong), I tried to create the bootable USB with 'Startup Disk Creator' in the -System-Administration menu. But the application doesn't load the .iso in the source disk image (I have the .iso in the Downloads folder). But I checked with another Kubuntu .iso and that loaded perfectly.

Can anyone suggest me a way to go about this?

Thanks!

---

### Post by Hakunka-Matata on 2011-08-10
I suggest trying unetbootin to load the USB stick, it's been very good to me.  link is in my signature

EDIT: after reading your post again.  The Ubuntu .iso you have in your Downloads folder, is it the same .iso you used to burn the CD?  Must be a good image if it worked with the CD.  

How much space do you have on the USB stick, is that a problem?  1 GiB is sufficient.  FAT32

---

