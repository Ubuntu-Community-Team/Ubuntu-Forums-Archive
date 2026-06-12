---
title: "How To Change Boot Order in Grub2 Menu"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-10-31
I tried editing the grub.cfg file using the sudo nano code but it seems to have not worked after a restart (file reverted back to the old and boot menu still the same). I know your not suppose to edit this file but I just gave it a shot as this is what I was use to with the old Grub bootloader. Anyway I read through the grub2 threads but havent found out how to get XP to be the first in the menu and then Ubuntu, Memtest, Recovery. All seem to refer to renaming, deleting, and adding new OS's to the menu. Any help appreciated.

I would like XP Home to be the first option in the grub bootloader and then Ubuntu.

---

### Post by Schendje on 2009-10-31
I don't know how to change the order, but you can use the Startup Manager (it's in Add/Remove or the Software Center) to select which one should be the default boot. You could change that setting to the XP one.

I'm not sure if it works with GRUB 2 though, so can't guarantee anything.

---

### Post by championboxes on 2009-10-31
Im not sure if this is the answer you are looking for but your answer should be found [here]("http://ubuntuforums.org/showthread.php?t=1306670") then after your changes are made you have to run the code ```
sudo update-grub
``` to update

---

