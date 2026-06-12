---
title: "Hosed ubuntu, time to reinstall."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by newbie1000 on 2008-12-30
I've learned enough to really hose my ubuntu.

I set it up to dual boot with Windows.

It's time to erase ubuntu and still leave windows on my machine,  and start over with a new install of ubuntu.

Anything stupid left for me to do?  :popcorn:

I actually would like to NOT screw this up.

---

### Post by DieB on 2008-12-30
Well first of all, do u have a seperate partition for /home?

if , not it might be helpful to back up all your working data, program setups, etc u do not want to get lost.

all user specific files of programs u will find in Nautilus(file-manager) if u turn on the show hidden files option under View.

so e.g. your saved games from wesnoth will be in the folder "/home/$user/.wesnoth"

hope u didn't forget about that ;)

---

### Post by RealG187 on 2008-12-30
Take all important information off obviously. I think you can deleted the partition and then just use "Guided: Use Largest Contigious Free Space" and you do not need to touch Window's partition.

---

### Post by handydan918 on 2008-12-30
> **newbie1000 said:**
> I've learned enough to really hose my ubuntu.

I set it up to dual boot with Windows.

It's time to erase ubuntu and still leave windows on my machine,  and start over with a new install of ubuntu.

Anything stupid left for me to do?  :popcorn:

I actually would like to NOT screw this up.

If you don't have any data on your Ubu system that you want, just pop the install cd in and reinstall to the same partitions. The only stupid thing left to do at that point is to install over your windows partition...

---

### Post by mkvnmtr on 2008-12-30
On my many reinstalls I always just put it back in the same place. Before starting the install open the partition manager on the live disk and identify all your partitions. Be sure yuo know which ones is which. Write them down if you need to. When you go to do the install they will have the same names. If you are not sure from the live disk you can post a picture here on the forum to ask. If you want to go back in the same place you can choose the manual install. When you get to the partition part you will see your partitions. Mark to format the one that is now your Ubuntu partition. You might need to label the mount point"/" or it might be marked for you. Don't change the other partitions. Click on proceed and it will be done back into the same partitions with your boot partition rewritten to reflect the new Ubuntu and the old windows. At any time up to the point of formating you can back out to the desktop to come to the forum to ask questions.

---

### Post by Desert Sailor on 2008-12-30
Don't want to Hi-jack this thread, but when you back up /home, does that save preferences and option settings in programs like Thunderbird, Firefox, OpenOffice ??

---

### Post by RealG187 on 2008-12-30
> **Desert Sailor said:**
> Don't want to Hi-jack this thread, but when you back up /home, does that save preferences and option settings in programs like Thunderbird, Firefox, OpenOffice ??
It should as the settings are stored in files in  the home folder.

example:

~/username/.mozilla
~/username/.openoffice

(Firefox and Thunder bird would probably both be in Mozilla)

---

### Post by thomasr on 2008-12-30
Best way I have found to backup and restore is Remastersys

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

[http://klikit.pbwiki.com/Remastersys](http://klikit.pbwiki.com/Remastersys)

---

### Post by markbuntu on 2008-12-30
You can reinstall without losing your /home. All you need to do is install in the previous partition and uncheck the format box in the partioner. The new install will overwrite all the files from the previous install and leave the /home directory alone.

---

