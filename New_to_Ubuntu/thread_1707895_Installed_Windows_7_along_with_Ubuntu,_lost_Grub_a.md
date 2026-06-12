---
title: "Installed Windows 7 along with Ubuntu, lost Grub and unable to boot into Ubuntu"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by theparasiticmin on 2011-03-15
Hello everyone. Not sure if this is the right place to post this but hopefully you guys can help. Initially I installed Ubuntu first and then openSUSE, but openSUSE didn't recognize Ubuntu in its bootloader. So I reformatted my computer (Dell Studio 1555) and installed openSUSE and then Ubuntu. Ubuntu's grub recognized both and I was able to boot into both. 

I made a partition out of the remaining free space and installed Windows 7 and for whatever reason I assumed Ubuntu would recognize Win 7 and add it to grub. Now, my laptop just automatically boots into Windows 7 and I don't see how to boot into Ubuntu or openSUSE. I installed Ubuntu from a USB pen drive, which has the option to load Ubuntu from USB, so is there any way to use this to reconfigure the bootloader? Sorry for block of text. Thank you!

---

### Post by Rabhak on 2011-03-15
Download ubuntu super grub bootloader here. 

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9797.iso)

and follow these steps in youtube

[http://www.youtube.com/watch?v=JFOmwZ-_zA8&feature=related](http://www.youtube.com/watch?v=JFOmwZ-_zA8&feature=related)


PS: Burn the grub image first. it is .iso

---

### Post by Jarpee on 2011-03-16
Did this work? And what exactly does the disc do when you follow the steps?

---

### Post by crispy_420 on 2011-03-16
You can also rebuild GRUB from the Ubuntu disc via commandline if you feel comfortable.

---

### Post by Jarpee on 2011-03-16
> **crispy_420 said:**
> You can also rebuild GRUB from the Ubuntu disc via commandline if you feel comfortable.

How do you do that? Any link it explanation would be greatly appreciated!

---

### Post by wilee-nilee on 2011-03-16
> **Jarpee said:**
> How do you do that? Any link it explanation would be greatly appreciated!

You should probably start your own thread out of courtesy, and explain your actual problem. Also if it is a boot problem click on the boot script link in my signature, run the script and post it in that thread, wrapped in code tags. If you in the reply window click on the **(#)** it creates the code tags paste the text between. 

This will give us a what is where and make it easier to address the problem.;)

---

### Post by cbowman57 on 2011-03-16
Easier to point you to the url.

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by crispy_420 on 2011-03-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

