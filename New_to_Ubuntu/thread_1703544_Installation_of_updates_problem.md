---
title: "Installation of updates problem"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by jeff martyn on 2011-03-09
Hi. I am using Ubuntu 10.10. When I want to add software updates using the update manager, I get the message:-
 
Failed to lock the package manager. Check if you are currently running another software management tool e.g.synaptic or aptitude. Only one tool is allowed to make changes at a time.
 
Details:-The packages are currently changed by apt-get.
 
As far as I can see, I am not not running any other prgram likely to affect the installation of updates. Can anyone advise me as to how I can stop this happening. Any help would be appreciated.

---

### Post by philinux on 2011-03-09
Have you tried a reboot.

---

### Post by fabricator4 on 2011-03-09
If you are definitely not running Synaptic or installing other programs, check to make sure you still have file

/var/cache/apt/archives/lock

Chris

---

### Post by adeee on 2011-03-09
reboot your computer.

---

