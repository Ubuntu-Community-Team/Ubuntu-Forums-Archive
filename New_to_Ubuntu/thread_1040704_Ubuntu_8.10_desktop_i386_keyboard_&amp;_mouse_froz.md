---
title: "Ubuntu 8.10 desktop i386 keyboard &amp; mouse frozen at login screen"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by CamNZ on 2009-01-15
Hi there, thanks for reading. Steps taken up until the problem occurred:

1. the latest release kernel '9' of Ubuntu was working fine for me until I fiddled around trying to set my Ext3 /home partition to 128 inodes in order for FS-Drive to be able to read /home via Windows XP. I downloaded GParted Live CD and reformatted my /home partition as Ext3 knowing that GParted formats using inode 128 (not 256 as Ubuntu had done). I also resized my NTFS and /home partitions. And viola! XP can read my Ext3 partition. I thought I was home free...

2. Next, because I did not understand the jargon on how to reset /home to the newly formatted Ext3 partition, I decided to reinstall Ubuntu using the same live CD as before, but this time without formatting the partitions (thereby keeping 128 inodes on my /home) So I do as said, Ubuntu installer told me that it would erase the data on / (root) partition but that's okay, it's just putting the same stuff back on again.

3. I reboot and select the top ubuntu kernel '9' in the boot menu and I find myself stuck at the login screen. Mouse and keys frozen. This was not my objective...

4. I reboot again using the 2nd ubuntu kernel '7' and back to the login screen but this time mouse and keyboard work! Logging out and back in again using Kernel '9' and I am back to the same frozen state.

5. I log back in again using ubuntu kernel '7' and here I am writing to you for help.

Anyone?

---

### Post by CamNZ on 2009-01-16
bump

---

### Post by CamNZ on 2009-01-18
I fixed this problem by booting using kernel 2.6.27-7-generic and running update manager. When the update was complete, I restarted and logged in using kernel 2.6.27-9-generic and the mouse and keyboard were no longer frozen.

---

