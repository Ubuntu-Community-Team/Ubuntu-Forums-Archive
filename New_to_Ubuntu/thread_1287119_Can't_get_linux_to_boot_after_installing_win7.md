---
title: "Can't get linux to boot after installing win7"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-09
Well, I installed win7 after fighting over partitions with it (it is incredibly picky).
 
I boot to windows, install easyBCD, add in a NeoGrub bootloader, and configure it with my backup of /boot/grub/menu.lst
 
So, then I go to boot, select NeoGrub and I get this:
Try (hd0,0):
 
And it freezes (although it might be Try ext (hd0,0) i can't remember and don't wanna reboot for a forum post.)
 
So, I was following a guide at ACP.
The Ubuntu wiki suggests I reinstall GRUB but won't this just make linux bootable and not windows?

---

### Post by cholericfun on 2009-10-09
grub will detect other OSs and make them bootable
its really only 3 lines in the terminal. go for it

---

### Post by Remagen on 2009-10-09
Jeeze, that was easy.
I just did that 3 line process to rebuild GRUB, and then *edited* 1 line in my /boot/grub/menu.lst file.

Windows & Linux happily boot.

Boom, Headshot, thanks cholericfun.

---

