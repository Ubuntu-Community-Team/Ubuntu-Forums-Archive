---
title: "Problem with package manager and update manager Ubuntu 10.10"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by arjunlalb on 2010-11-26
Hi, I'm pretty new to daily linux usage,but kind of intermediate user.. I encountered the following problem last day while installing the program bandwidthd, it did not completely install.
Later when I try to install other packages, it says tht bandwidthd is not properly installed and try reinstalling it before installilng other packages, when I tried to reinstall,I couldnt make it due to an error which said tht it cannot find the archive.
Later I tried many ways found in the internet to fix the problem,but I couldnt. Now I'm unable to open package manager or update manager and is unable to install any programs.
I get the following error now

"E: The package bandwidthd needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Please help me... :-(

---

### Post by Foxheadz on 2010-11-26
Try opening a terminal window and typing ```
sudo apt-get remove bandwidthd
```

---

### Post by arjunlalb on 2010-11-27
I tried tht..it says

"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package bandwidth needs to be reinstalled,but I can't find an archive for it."

---

### Post by MooPi on 2010-11-27
You could try a couple of things. ```
sudo dpkg --configure -a
``` This should try to correct partial installs. If you get errors with that try, ```
sudo apt-get update
sudo apt-get purge bandwidth
sudo apt-get install bandwidth
```

---

### Post by arjunlalb on 2010-11-28
still not working... :(

"arjunlal@Arjun-DT:~$ sudo apt-get purge bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bandwidthd*
0 upgraded, 0 newly installed, 1 to remove and 112 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)"

---

### Post by arjunlalb on 2010-11-30
Thanks to all.. the problem is solved... I was unable to resolve with the above steps... tries something else too and it worked..

---

### Post by tajiknomi on 2010-11-30
> **arjunlalb said:**
> Thanks to all.. the problem is solved... I was unable to resolve with the above steps... tries something else too and it worked..


[SIZE=2]Can you post ,what you *did to **fix** it*....> so that someone got this same-problem in Future and may fix his/her....[/SIZE]



Moreover,Mark the thread as Solved in thread-tools:p

---

