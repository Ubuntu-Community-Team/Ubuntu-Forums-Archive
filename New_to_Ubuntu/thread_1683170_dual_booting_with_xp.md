---
title: "dual booting with xp"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by bobenk on 2011-02-07
I have loaded ubuntu 10.04 in my laptop along with windows xp. Working ok for a long time. Now I am not able to load xp. When selected system reboot and shows the slection panel again. Ubuntu is working fine. Can anybody tell why xp become inaccessible suddenly.

---

### Post by jonnny_j22 on 2011-02-07
It's usually a grub error.

First try 

sudo update-grub

then, if still no luck have a look in

sudo gedit /etc/default/grub

to look for any obvioous settings that are wrong - like there is no windows entry, the wrong partition or drive is listed or the entry has become hashed out.

If you make any changes, sudo update-grub.

Then if still no luck, reinstall grub, and - you've guessed it... 
sudo update-grub

After that, you're really looking at a hard drive or win xp issue.

you can check the hdd for errors with fsck  (with all partitions unmounted)

Windows xp - it'll have to be a repair install - note that atfter this you'll have to reinstall grub... again.

---

### Post by ajgreeny on 2011-02-07
Does XP appear in the grub menu, or is it missing from there?

---

