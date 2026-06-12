---
title: "What do I do to install Adobe Flash Player?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by AlexOslo on 2009-11-11
Just got 9.10, and a pop-up window says I need to install Adobe Flash Player.
I tried following the command found here: 
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

```
[username]@[username]-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
```

What can I do to rectify the situation?

---

### Post by fluxbuntu on 2009-11-11
Run.... 'apt-cache search flash player'. That'll show you everything in the repos pertaining to flash. Find what you want and then 'sudo apt-get install (whatyouwant)'

---

### Post by oldos2er on 2009-11-11
> **AlexOslo said:**
> Just got 9.10, and a pop-up window says I need to install Adobe Flash Player.
I tried following the command found here: 
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

```
[username]@[username]-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
```

What can I do to rectify the situation?

 Make sure you have the multiverse repository enabled. If you're running 32-bit Ubuntu, run ```
sudo apt-get install flashplugin-installer
``` If you're running 64-bit Ubuntu, see [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

---

### Post by Monsuco on 2009-11-11
> **oldos2er said:**
> Make sure you have the multiverse repository enabled. If you're running 32-bit Ubuntu, run ```
sudo apt-get install flashplugin-installer
``` If you're running 64-bit Ubuntu, see [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)
After enabling multiverse you need to do ```
sudo apt-get update
``` first then do the install command. If you enable multiverse through software sources or synaptic it will ask you to reload.

---

### Post by AlexOslo on 2009-11-11
> **Monsuco said:**
> After enabling multiverse you need to do ```
sudo apt-get update
``` first then do the install command. If you enable multiverse through software sources or synaptic it will ask you to reload.
Most helpful -
I entered ```
sudo apt-get update
``` in the monitor, and the packages installed themselves. When the pop-up bar reappeared upon closing and restarting Firefox, I chose "install missing plugins" (which now worked fine - previously hadn't).
Looks to be working very well.

---

