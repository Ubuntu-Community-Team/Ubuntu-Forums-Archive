---
title: "Weird - gdm freezes if I connect a second USB drive"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by sarc on 2010-11-16
I run 10.4 from an external USB hard disk drive.  If I connect another USB hard disk drive (even a blank drive) gdm freezes, all my icons disappear from desktop, and I have to pull the power plug to reboot.  If I connect a USB flash or SD card then everything is fine.  Any ideas what I can do?  Thanks!

---

### Post by georgemc on 2010-11-16
> **sarc said:**
> I run 10.4 from an external USB hard disk drive.  If I connect another USB hard disk drive (even a blank drive) gdm freezes, all my icons disappear from desktop, and I have to pull the power plug to reboot.  If I connect a USB flash or SD card then everything is fine.  Any ideas what I can do?  Thanks!
 

 I had some thing similar happen to me when I plugged in certain devices.  The desktop and cpu froze and I had to hard power down and reboot.  Not sure if this is what you are experiencing.
 

 What worked for me was to add the “irqpoll” boot option to grub.  As you are running 10.04 you most likely have grub2 installed, edit the file “/etc/default/grub” with your favorite text editor, I use gedit, and then update grub.
 

 ```

 sudo gedit /etc/default/grub
 
``` Look for the line “GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add “irqpoll”.  Should look like this after the edit:
 

 ```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"
 
``` Save this and then I run:
 

 ```
 
 sudo grub-mkconfig -o /boot/grub/grub.cfg
 
``` Re-boot and check the log files and make sure the boot options are there and see if that does the trick.
 

 If that doesn't help then you might have to look into “udev” and fiddle around with that.
 

 Hope this helps.
 

 George
 

 References:
 [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)
 [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

