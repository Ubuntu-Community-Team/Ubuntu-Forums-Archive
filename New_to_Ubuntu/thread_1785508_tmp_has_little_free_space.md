---
title: "/tmp has little free space"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by cjv8888 on 2011-06-18
I use Audacity to transfer records into the computer.  By default, it uses the /tmp file which used to have a space equal to the /.  I believe I installed Ubuntu Tweak.  Soon after the /tmp file shows a free space of 1.9 GB only.  I know I can change the default file used by Audacity but this puzzles me.
What caused the /tmp file to only have a free space of 1.9 GB?  And how can I remove this space restriction?  / has free space of 20 GB.

---

### Post by Bucky Ball on 2011-06-18
Try emptying the /tmp file.

---

### Post by cjv8888 on 2011-06-18
Property:
337 items, totalling 11.4 MB
(some contents unreadable)

Location: /
Volume:  unknown

Free Space: 1.9 GB

How do you empty the tmp folder?

---

### Post by Bucky Ball on 2011-06-18
Easiest way is to go to the /tmp directory, hit control+h to show hidden files, select everything and delete. If that refuses you permissions, open a terminal (Applications>Accessories>Terminal) and issue this command:

```
sudo nautilus 
```

(presuming you are using Gnome), which will open your file manager with you as root. BE CAREFUL what you delete while root and close the root file manager as soon as you're done. Go to /tmp and use the process outlined above: show hidden files, select all, delete.

---

### Post by oldos2er on 2011-06-18
Be very careful about deleting data in /tmp while your system is up and running. Many programs store potentially sensitive data there. 

/tmp is cleared on reboot.

Do you have /tmp on its own partition?

---

### Post by cjv8888 on 2011-06-18
I have / on a 20 GB partition and /home on the rest of the disk.

---

### Post by LowSky on 2011-06-18
Tell Audacity to use your /home folder if it has more space.

Open Audacity, click EDIT > Preferences.
Go to Directories choose a new location, and if needed create a new folder too.

---

### Post by cjv8888 on 2011-06-18
> **LowSky said:**
> Tell Audacity to use your /home folder if it has more space.

Open Audacity, click EDIT > Preferences.
Go to Directories choose a new location, and if needed create a new folder too.

I have done that already, thanks.  It still puzzles me.  Is there any way to get back the free space of the /tmp short of a re-installation of the system?

---

