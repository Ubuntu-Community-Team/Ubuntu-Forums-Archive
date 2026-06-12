---
title: "Trouble installing - please help"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by jemmar on 2009-04-26
Hi,

Sorry, this is so long. Please excuse my ignorance! I'm totally new to linux, and I think I've messed it all up already!

I'm having some problems installing ubuntu on my samsung nc10. I have the installation on my usb drive. I wanted to install it side by side with XP, so I selected the option for it to install side by side and work out the partition sizes by itself. During the installation a message came up saying "executing 'grub-install /dev/sda' failed'. I clicked OK and the installation finished. It seemed to work ok, and at the time I didn't know what grub was (I'm totally new to linux).
I restarted my comp, but I didn't get a choice to which OS to use and it went straight to XP.

I looked around on the forums and found what grub was and how to fix it (I restarted my comp and booted from the usb drive so I could use the disc version of ubuntu, and fixed it in terminal). I restarted again like the guide said to, and instead of the grub menu, the grub cli came up. I don't know any of the commands to get into ubuntu or XP from there. 
My stepdad suggested re-installing ubuntu, seeing as grub was definitely installed now, and he thought it would write over the existing installation. I did that, but it just created another partition, and I got the same error about grub as before.
So now, I have ubuntu installed twice, I still have XP, but I can't get into any of it because I can't get past the grub cli. The only way I can use my comp at the moment is to use the disc version from the usb drive.
My stepdad then suggested deleting the partitions with ubuntu on them and starting again, but as I can only use the disc version of ubuntu, the partition manager says that the partition is in use and so I can't delete it!

Sorry this is so long, I hope someone can help me sort this out!

---

### Post by steve101101 on 2009-04-26
well if you use the "super grub disk" which you can download online. this should restore grub so that you can boot into xp as well as ubuntu. after this works you will need to get rid of the 2nd ubuntu partitions and expand the 1st ubuntu partition to make use of this extra space.

---

### Post by presence1960 on 2009-04-26
my bad wrong thread

---

### Post by steve101101 on 2009-04-26
click this link to download the iso [http://forjamari.linex.org/frs/download.php/1138/super_grub_disk_0.9783.iso](http://forjamari.linex.org/frs/download.php/1138/super_grub_disk_0.9783.iso)

burn onto disk

restart and boot into super grub

---

