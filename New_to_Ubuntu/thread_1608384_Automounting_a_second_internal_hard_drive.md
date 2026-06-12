---
title: "Automounting a second internal hard drive"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Chrispy764 on 2010-10-29
I am fairly new to Ubuntu and have 2 hard drives in my computer. The links below have helped me automount my second hard drive. This is probably not something new but I found that if I set the mount point to /home/'user' the second hard drive becomes my home folder. This is cool with me since I used to copy my files to my 2nd hard drive as a backup in case I had to reinstall Lucid and now all of my files that default to the "home" folder are now going to my data drive. My question is has anyone else tried this and are there any issues about doing this? I do know that if I have to reinstall Ubuntu, I will have to remount the drive again, but at least all of my files will be there.

[http://ubuntuforums.org/showthread.php?t=1604829](http://ubuntuforums.org/showthread.php?t=1604829)

[https://help.ubuntu.com/community/Fstab#Editing%20fstab](https://help.ubuntu.com/community/Fstab#Editing%20fstab)

---

### Post by ArgusVision on 2010-10-29
Yes, what you are doing has been done without any real trouble. It's similar to what some people do by preference with a separate /home partition on the same physical drive. An advantage to what you have set up is that if your primary drive fails you still have your data on a secondary drive, just install OS to a replacement primary and you'd be set. You still want to be sure to backup the data on the secondary drive just incase it fails.

---

