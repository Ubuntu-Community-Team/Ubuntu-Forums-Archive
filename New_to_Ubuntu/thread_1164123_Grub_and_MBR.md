---
title: "Grub and MBR"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by ChrisB111 on 2009-05-19
I run Ubuntu Intrepid off my external hard drive, I use a floppy bootloader called PloP to chainload Grub on the hard drive as my computer has no usb boot support. I want to install Jaunty on another partition so I can run both systems. 

Can someone explain to me how the whole MBR bootloader thing works and if/how it would be possible to install both to the hard drive and choose what ubuntu system to boot. I have been looking around on the internet for a while now trying to learn about the whole bootloader partition thing but don't feel like I have got anywhere.

Thanks,

Chris

---

### Post by MegaJim on 2009-05-19
Easiest way to put grub on your HDD is boot up a ubuntu live cd and install it on the command line

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

stage1 should be on your external disk, assuming thats where you want to keep it

---

### Post by ChrisB111 on 2009-05-19
> **MegaJim said:**
> Easiest way to put grub on your HDD is boot up a ubuntu live cd and install it on the command line

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

stage1 should be on your external disk, assuming thats where you want to keep it

Thanks for the quick reply, but what I want to know is how to make it boot two Ubuntu systems and how to install jaunty from a live cd with this in mind.

Thanks,

Chris

---

### Post by MegaJim on 2009-05-19
Ah I see, well if thats what you really want to do, this guide should help [http://ubuntuforums.org/showthread.php?t=724817]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by ChrisB111 on 2009-05-19
I think that was the info I was looking for.

Thanks again,

Chris

---

