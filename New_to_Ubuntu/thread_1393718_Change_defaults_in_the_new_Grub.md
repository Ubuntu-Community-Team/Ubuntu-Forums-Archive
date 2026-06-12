---
title: "Change defaults in the new Grub"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by veggen on 2010-01-29
Since installing Karmic (and with it a newer version of Grub), I can't seem to find /boot/grub/menu.lst. Which file is now used to set the default OS to load? I need to delete some superfluous entries in the Grub menu and the reset the default to WinXP...

Thanks!

---

### Post by inobe on 2010-01-29
their ya go

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by themusicalduck on 2010-01-29
If you install a program called StartUp-Manager from the software centre, that lets you change the default and other things. Although it's a good idea (I've found from experience..) after using that program to run ```
sudo update-grub
``` in a terminal to make sure everything continues to work .

---

### Post by veggen on 2010-01-29
Cool, thank you guys! After seeing the first reply, and went on and manually did all the changes, but I'm very happy to see I won't be needing to repeat that!

---

