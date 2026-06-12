---
title: "Loading Screen &quot;Out of Range&quot;"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by BlueTesla on 2009-03-05
When booting my computer, the loading screen wont display, all it shows is "Out of Range" on my monitor. If I hook up an old CRT it displays fine so I'm guessing it's a resolution thing with my LCD monitor running at 1680x1050. Is their an option I can change somewhere so that it displays? I know it's a minor gripe but I'd really like to fix it. It's been months and it's starting to bother me :p

Just FYI everything else works perfectly, it's just the loading screen with resolution problems.

Thanks for your time!

---

### Post by SuperSonic4 on 2009-03-05
You need to boot to a lower resolution, the Out of Range usually means that the frequency/resolution from the GPU is too high and enabling low graphics mode in boot should help

---

### Post by tarps87 on 2009-03-05
Try adding vga=786 to the end of the boot line in the grub boot menu

```
sudo gedit /boot/grub/menu.lst
```
add vga to the end of this line
kernel /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro quiet splash
e.g.
kernel /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro quiet splash vga=786

This table might help:
```
      colour          depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795
```

The table was taken from post 2 on this thread [http://ubuntuforums.org/showthread.php?t=185619](http://ubuntuforums.org/showthread.php?t=185619)

---

