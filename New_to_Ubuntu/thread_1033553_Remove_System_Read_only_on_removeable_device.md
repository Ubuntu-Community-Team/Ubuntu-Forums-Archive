---
title: "Remove System Read only on removeable device"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by cerealtx on 2009-01-07
Okay so the device is my ipod and i have 100 gb of files (not songs not videos it just comes up as "other") i try and use gtkpod to remove them but i have to load them all first and gtkpod freezes so i went into /media/IPOD/iPod_Controls/Music and theres 49 Folders F00 - F49 all with files labeled gtk#####.mp3 can't delete them not even as root any ideas?

```
root@cereal-laptop:/media/IPOD/iPod_Control/Music/F00# rm -rf *
rm: cannot remove `gtkpod003489.mp3': Read-only file system
rm: cannot remove `gtkpod007116.mp3': Read-only file system
rm: cannot remove `gtkpod009457.mp3': Read-only file system
rm: cannot remove `gtkpod014530.mp3': Read-only file system
rm: cannot remove `gtkpod022292.mp3': Read-only file system
rm: cannot remove `gtkpod023054.mp3': Read-only file system

```

---

### Post by shifty_powers on 2009-01-07
have you tried sudoing that command?

```
sudo /media/IPOD/iPod_Control/Music/F00# rm -rf *
```

---

