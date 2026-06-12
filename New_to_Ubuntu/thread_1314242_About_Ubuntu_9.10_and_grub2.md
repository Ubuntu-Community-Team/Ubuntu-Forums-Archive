---
title: "About Ubuntu 9.10 and grub2"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by PLIACHAS PASCHALIS on 2009-11-04
i had an installation of ubuntu, vista and xp Os'es on my hard disk. After i upgraded in 9.10, grub2 replaced grub as boot manager. after that i couldn't boot to vista or Xp. So after i read some post i uninstalled grub2 and restored grub.
Does anybody know how this entry in menu.lst can converted in grub2 and work?

''''''''''''''''''''''''''''''''''''
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
hide (hd0,1)
unhide (hd0,0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
hide (hd0,0)
unhide (hd0,1)
chainloader	+1
'''''''''''''''''''''''''''''''''

Thanks for help

---

### Post by ukripper on 2009-11-04
This may help you understand Grub2
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=customize+grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=customize+grub2)

---

### Post by PLIACHAS PASCHALIS on 2009-11-04
I saw it but i couldn't find how to hide and show the partition with new commands of grub2. Thanks for your reply

---

### Post by philinux on 2009-11-04
You say upgrade. I think you mean a clean install.

Grub2 can fail to detect other operating systems on a new install. However all you needed to have done was, well ask on here first would have been good, open a terminal and run...

```
sudo update-grub
```

This would then have picked up vista and xp.

---

