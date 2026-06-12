---
title: "Need help installing Ubuntu 11.04 with W7 dual boot (ver.2)"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by mystvearn on 2011-05-26
My W7 was wiped out by the first install, now I am left with an unused partition and a 30gb ubuntu partition and more work to get my data and W7 back on. Details are in the thread below:
[http://ubuntuforums.org/showthread.php?t=1767533](http://ubuntuforums.org/showthread.php?t=1767533)

I want to install W7 and dual boot in the unallocated partition? Is it possible to install W7 directly onto the unused partition using the dvd and will it dual boot with GRUB prior to loading screen or must I wipe out everything and start fresh?

---

### Post by Fadingfool on 2011-05-26
Not having used Win 7 you are free to ignore this post :) but as a Vista and Ubuntu (10.04) user I found it was easiest to wipe the drive with a fresh install of Vista (format drive and partition the whole drive as a Vista drive) and then install Ubuntu after.
I have my drive setup with a 500 GB windows partition (mainly games), 100 GB Ubuntu and the rest as swap space (probably over kill but I like neat numbers (probably OCD))
Ubuntu is used to being set up on a window's drive, I get the feeling windows is not used to playing second fiddle.

---

### Post by mystvearn on 2011-05-26
Trying this solution first:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Will let you know if I need help. Otherwise, installing windows, and uploading data to computer takes a lot of time.

---

### Post by Fadingfool on 2011-05-26
Probably worth trying if you are confident in recovering grub after the windows install.  Last time I did a complete wipe and install it took about half a day (including downloading various games from steam) - an external drive with all the windows service packs and dell specific drivers certainly reduces the amount of time required (funnily enough the ubuntu bit didn't take long at all) . 
  I'll probably end up doing a fresh install with the next LTS ubuntu release.
  Oh the windows partition ended up being named "windows recovery partition" in grub the last time I installed Ubuntu - I should get round to changing it sometime (only just got rid of the previous kernals listed on the grub menu) - so don't be suprised if your grub menu has something like that after the ubuntu and memtest options.

---

