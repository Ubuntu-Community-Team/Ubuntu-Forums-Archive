---
title: "[SOLVED] Using GParted to resize my HD for XP"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-12-25
I just did a clean install of ubuntu 8.10 on my Acer laptop so that it uses the entire HD (160gb).  But now I'm wondering if I can resize that 160GB so that I can install windows XP on it for gaming (I already use Virtualbox but gaming on it sucks).  I'm thinking like 40GB for XP and the other 120GB for Ubuntu.

I just installed Partition Editor from Add/Remove but have no idea how to use it.  This is the readings of my HD when I open up Partition Editor:
/dev/sda1      ext3          142.96gb             boot
/dev/sda2      extended      6.09gb
 /dev/sda5     swap          6.09gb

Thank you!

---

### Post by taurus on 2008-12-25
You cannot use gparted from Ubuntu to resize /dev/sda1 because you cannot resize a partition while you are using it.  Therefore, you have to use gparted from either the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by billgoldberg on 2008-12-25
Well to start with you can't format the partition Ubuntu uses from Ubuntu itself.

You will need the live cd, and boot from that.

Read here for more info:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

When you are done resizing, pop in your XP drive and make sure you install XP on the correct partition.

After XP is installed, you'll notice the grub is missing and your pc will boot straight into Windows.

Download a copy from the "super grub disk", burn the image and boot from it.

Use it to reinstall the grub, restart the pc and boot Ubuntu and once there, do this:

[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_132.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_132.html)

(in Ubuntu use the command "fdisk -l" to find out on which partition windows is on. If it's on hda2, use "hd (0,1)" )

---

### Post by FAMUgolfer on 2008-12-25
Thank you very much for your quick replies.  I will try your suggestions and reort back to this page.  It seems though that this may take at least a day!!!...Oh well I'm up for the challenge.

---

### Post by taurus on 2008-12-25
You can recover GRUB with the LiveCD too so no need to download an extra stuff.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by FAMUgolfer on 2008-12-25
> **billgoldberg said:**
> 

Download a copy from the "super grub disk", burn the image and boot from it.

Use it to reinstall the grub, restart the pc and boot Ubuntu and once there, do this:



What does this mean "super grub disk"?? Thank You

---

### Post by zvacet on 2008-12-25
It means [this.]("http://www.supergrubdisk.org/") You can reinstall grub as **taurus** adviced.

---

### Post by FAMUgolfer on 2008-12-25
Thank you everyone!!!!

IT WORKED!!!

The only thing though is that I had to change SATA Mode in BIOS to IDE.  Not sure why, but besides this it's a thing of beauty!

Also, on this website [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5) they didn't mention to type in "savedefault" when adding Windows XP to GRUB like the link billgoldberg said for me to follow [http://www.linuxtopia.org/online_boo...index_132.html](http://www.linuxtopia.org/online_boo...index_132.html)

Will this be a problem? Thank you.

---

