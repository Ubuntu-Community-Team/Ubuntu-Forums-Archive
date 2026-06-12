---
title: "Stuck at initramfs"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by dileepdinesh on 2009-03-24
Hi, i have a HP laptop,,, i have installed ubuntu 8.04 inside vista.....
now i have this problem, when i boot ubuntu, the splash screen comes, and then a terminal type window comes and says its busybox,,,and the prompt looks like this
(initramfs):
I am just a beginner, and have some of my project files inside ubuntu, so i dont want to reinstall,,,I tried rebooting manytimes,, but this is the situation,, i tried some solutions after googling like updating this initramfs but still it didnt work out,,,,,,

---

### Post by blazemore on 2009-03-24
When you say you installed it "Inside Vista", do you mean using Wubi?

If so, try uninstalling from Add/Remove.
Reboot your computer
Install again.

I've had this issue in the past, and this solution has worked for me.

However, I would recommend a "full" installation onto bare-metal.

---

### Post by jmszr on 2009-03-24
dileepdinesh,
               Wubi installs Ubuntu into a windows folder usually a NTFS type of file system. this file system has a known reaction of being unstable in other operating systems like Ubuntu.. because people sometime fail to unmount the drive correctly, heck even Windows can be blamed for this.
Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make sure "Automatically fix file system errors" is checked and click Start. After the checking is done, restart the pc by using the start menu(Do Not hard reboot) and try using Ubuntu now. (From Wubu Wiki)
 
The immediate previous tip can also be accomplished by running chkdsk/f in Vista.

---

