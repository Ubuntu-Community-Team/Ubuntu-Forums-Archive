---
title: "How to change home folder?"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-21
I've been messing around with my partitions and dual booting, and I've run into what I think is a problem. When I go into terminal, the home command "name@namepcdm062~$" goes to the directory in my main filesystem (250gb), and not into the 118gb filesystem that I've set up for Ubuntu. How do I change where the main home directory is? I don't want all of my documents and downloads to be on my main filesystem, but instead onto the 118gb partition I made for Ubuntu. Also, the 188gb partition is inside of the main filesystem in the directory.

---

### Post by doas777 on 2011-07-21
well, ubuntu will always map your home to \home\username (I;m sure you can change that but it would be a bad idea), so usually whenever someone wants to do what you are doing, their best bet is to:

1) move your content (your \home\username folder and all sub-files\folders) off to the new drive. delete if off the existing drive.  Leave an empty \home folder in \ .
2) edit your fstab to mount your new drive to \home\
3) reboot.

so, in the end, your home is still in \home\username, but the data in that folder is actually on a different drive from root.

this shoudl provide you all the info you need:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

