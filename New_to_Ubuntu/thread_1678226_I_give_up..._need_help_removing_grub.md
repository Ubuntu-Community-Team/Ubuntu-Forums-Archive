---
title: "I give up... need help removing grub"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by krismx6920 on 2011-01-30
I have a new lap top and tried to install ubuntu to the hard drive..  I can not get it to load...  Installed on usb can not get it to load...  I think it doesn't recognize video card (intel hd)...  tried startx just locks up..  I need to remove grub so I can remove ubuntu from hard drive..  deleted ubuntu partition and I couldn't even boot windows..  please help...

---

### Post by garvinrick4 on 2011-01-30
When you put Windows grub back you will overwrite the Ubuntu's grub so no need to 
worry about. Here is link on how to replace windows grub: Pretty simple really.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
If you do not have your windows disks report back there is a way to do it with Ubuntu disk.
Called lilo:

---

### Post by garvinrick4 on 2011-01-30
Ubuntu is easy to install with a bit of knowledge if you need to ask questions about
what went wrong ask here lots of users to help you out, that is what they are here for
to give back what they received at one time.

---

### Post by krismx6920 on 2011-01-30
I've tried to get help but i will give it another shot..  I was using an old gateway with no hard drive and booting from a external flash drive and/or external hard drive.  I got a new laptop on monday and at first the usb drive booted fine..  It was missing some sensors but worked well..  I partitioned my hard drive and allowed 50gb for ubuntu 10.10...  Booted it up, grub came up selected ubuntu and a whole bunch of script started running by on screen.. on old computer just got a cursor then gui popped up and I was all set to run it...  Eventually it asks for log in and password.. once i input my info it brings me to my kris@...$prompt but gui does not start..  someone recommended startx, but this just locked the computer.  somehow I managed to get a second 50gb partition on my hard drive with ubuntu installed..  The flash drive that was working came up with it's own grub with 2 boots options, i beleive .22 and .24... neither one worked... got 4 mount errors..  I have seen an error message like gave up on waiting for intel hd...  tried recovery mode nothing...  when i deleted one partition computer just locked up and would not boot... this was all 32bit version... tried 64 bit on flash drive same result...  I can boot from cd..  I really like linux but really frustrated..

---

### Post by garvinrick4 on 2011-01-30
If you still need some help.
Put your live cd in and open gparted and take a screenshot and post it here using
the attachments in Message box. It is best we start over and put install and get grub2
in the mbr of sda. gparted will show us what you got going on drive right now.
If you can also download this script in live cd to desktop and then run the code I give
you and post it to this thread.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```
After you post it to this thread highlight it and hit the little # sign in
upper right corner of message box and will make easier to read.

---

