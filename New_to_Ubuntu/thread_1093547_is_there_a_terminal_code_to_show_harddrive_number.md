---
title: "is there a terminal code to show harddrive number?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by billmik on 2009-03-11
Ive noticed a problem during shutdown i get a error of some king (libhal shut down failed) then it shuts down. So i wanted to do a scan disc make fsck to run by using sudo tune2fs -c 1 /dev/sda1. But im not sure what drive number is ubuntu installed on. Is there something i could type in terminal to show the number, because im not sure sda1 is the right drive.  Or is there someway better to do a scan disc.

---

### Post by kanikilu on 2009-03-11
Type ```
mount
``` You should see a line like this ```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
```

---

### Post by billmik on 2009-03-11
got it thanks

---

### Post by ajgreeny on 2009-03-11
Having found the right partition, you can make the system do a check with the command ```
sudo touch /forcefsck
```and next boot that partition will be checked.  There is no need to use tune2fs, which will then need to be rerun to set the normal higher number after rebooting.

---

