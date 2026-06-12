---
title: "Grub problem"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by mosquetero on 2010-09-01
Hi all!

I have in my computer two operating systems: Ubuntu 9 and Windows VISTA. Today, I booted my laptop and I chose the wrong Windows Vista with Grub. When I realized, I restarted the laptop manually and now, when Grub is loading the subsequent sentence appears:

GRUB loading. Please wait...
ERROR 22

Anyone can help me to recover normality please?

---

### Post by oldfred on 2010-09-01
To get error 22 you must be still using old grub?

[http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22)

To reinstall grub legacy:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by mosquetero on 2010-09-01
Thanks. I tried How to restore the Ubuntu grub bootloader (9.04 and older) but when I type find /boot/grub/stage1 I get this error 15 file not found. Does it ring any bell?

---

### Post by jtarin on 2010-09-01
Try to reinstall Grub not restore.

---

### Post by jtarin on 2010-09-01
> **mosquetero said:**
> Thanks. I tried How to restore the Ubuntu grub bootloader (9.04 and older) but when I type find /boot/grub/stage1 I get this error 15 file not found. Does it ring any bell?
[You'll have to find it by trial and error]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").....When in the Live CD environment you will have to "chroot" and search your boot directory for the exact path to the file.

---

### Post by oldfred on 2010-09-01
If you need more help, from liveCD download and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

