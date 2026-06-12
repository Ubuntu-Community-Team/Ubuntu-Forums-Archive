---
title: "Need to boot vista, Complicated problem"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by _DeepBlue on 2010-03-28
long story short, i just reinstalled vista, and grub still works. it lets me boot karmic, but it still thinks the windows partition is XP, and when i select it I get an error, and cannot boot windows (which is now vista, not XP anymore). Any ideas? thanks in advance!

---

### Post by PocketDog on 2010-03-28
Your configuration may have changed, but grub hasn't. ```
sudo update-grub
``` in terminal, and reboot. That should reconfigure grub to see your new system config

---

### Post by bumanie on 2010-03-28
As long as you are confident in reinstalling grub 2, you could go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), download the vista repair cd and see if that fixes vista and removes all traces of xp files from the mbr. If so, simply reinstall grub.

---

### Post by _DeepBlue on 2010-03-28
> **PocketDog said:**
> Your configuration may have changed, but grub hasn't. ```
sudo update-grub
``` in terminal, and reboot. That should reconfigure grub to see your new system config

ill try that now! 

> As long as you are confident in reinstalling grub 2, you could go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), download the vista repair cd and see if that fixes vista and removes all traces of xp files from the mbr. If so, simply reinstall grub.

Vista files are all there, im assuming its a boot problem.. ill try what pocketdog said, hopefully it works! :D

---

### Post by m4tic on 2010-03-28
if update-grub fails then its sudo update-grub2

---

### Post by _DeepBlue on 2010-03-28
> **PocketDog said:**
> Your configuration may have changed, but grub hasn't. ```
sudo update-grub
``` in terminal, and reboot. That should reconfigure grub to see your new system config


Wow, was as simple as that. Big up PocketDog, thank you SO much! :D:D:D

---

### Post by PocketDog on 2010-03-28
It's a pleasure. :)

---

