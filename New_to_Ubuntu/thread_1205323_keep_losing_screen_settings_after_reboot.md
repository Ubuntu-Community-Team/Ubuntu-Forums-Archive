---
title: "keep losing screen settings after reboot"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by super newbie on 2009-07-05
hi all, every time i reboot, my screen resolution is set to 600x800 and i have to go to System-Administration-NVIDEA X Server Settings and from there i can set the proper resolution.  i then choose "Save to X Configuration File" and then i'm told "Unable to create new X Config backup file '/etc/x11/xorg.conf.backup'  Is that what i'm supposed to do?  Does it have something to do with root privliges?  thanks

---

### Post by Ocxic on 2009-07-05
I had the same problem, you have to remove/backup the original file first.

"sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bk"

Then you will be able to save properly. You also have to run the nVidia Settings as root.

---

### Post by RedRat on 2009-07-05
> **super newbie said:**
> hi all, every time i reboot, my screen resolution is set to 600x800 and i have to go to System-Administration-NVIDEA X Server Settings and from there i can set the proper resolution.  i then choose "Save to X Configuration File" and then i'm told "Unable to create new X Config backup file '/etc/x11/xorg.conf.backup'  Is that what i'm supposed to do?  Does it have something to do with root privliges?  thanks

If you are running Ubuntu use this in the terminal window:
gksudo nvidia-settings
Then you are running as root and it will save your settings.

---

### Post by frunns on 2009-07-06
> **Ocxic said:**
> I had the same problem, you have to remove/backup the original file first.

"sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bk"

Then you will be able to save properly. You also have to run the nVidia Settings as root.

Why on earth should he move the file? Only that'll do is mess up any other configurations he has in it...
If you use it often you could right click it, add it to the panel and then change properties of the icon on the panel to have 'gksudo' before the command (I switch between external display and internal every few days, so this is how I do it).

---

### Post by Ocxic on 2009-07-06
X11 stopped using the xorg.conf file for since 8.10 i believe. and there is really no reason to modify it nowadays anyway unless your trying to do something very specific. not to mention the the nVidia setting s app cannot parse the almost empty file.

---

### Post by super newbie on 2009-07-07
i've tried "gksudo nvidia-settings" and it semmed to save the file just fine...but i still have the same problem.  i've compared the file nvidia is creating with the one that is stored in my X11 folder and they are the same.  here is what's in my X11 folder...is this correct?

---

### Post by sphynk on 2009-08-20
gksudo nvidia-settings

...and saving settings as root solved my "losing display settings on reboot" problem on Hardy Heron. Many thanks RedRat.

---

### Post by Immolatus on 2009-08-20
This is what you want -->[http://ubuntuforums.org/showthread.php?t=965398](http://ubuntuforums.org/showthread.php?t=965398)

---

