---
title: "Software RAID 5 will not automount on boot"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by blackwatchplaid on 2010-07-22
Not sure if this is really beginner... if not maybe one of the mods can move this to the appropriate spot in the forums.

At any rate, I have a fresh install of Ubuntu 10.04 Desktop.
Clean build, using it as a home server: 4- 1.5 TB drives in a software RAID 5 array, ext4 partition for a total of about 4.4 TB effective storage.  The root filesystem is on a 42 GB partition of SATA 1 on the board, or /dev/sda as Ubuntu sees it.

Thought about running the 10.04 server edition, but I knew I wanted to run Vuze, PS3 media server, and possibly hook it directly to the television, and so thought that keeping the GUI would be to my advantage.

I set up the softRAID using mdadm, technically.  But I did it using the GUI in :Launcher>System>Disk Utility from the main panel. (Not sure if this makes a big difference in how the config looks)

So the file system boots just fine, and the RAID array shows up upon each login.  The only issue I haven't been able to resolve is how to set the array to auto mount either at initial boot or each login.  It mounts to /media/"array name" as soon as I click on the array listed in "Computer" so this isn't a crucial issue, just one that I'd like to know how to solve for future builds.

I've tried:

1) modifying /etc fstab
- listing RAID name (/dev/md0)
- where it mounts when I start the array after logging in (/media/arrayname)
-file system type (ext3/ext4)

2) Hunting the Ubuntu forums for similar problems.  No luck so far.

Can anyone help me out?

---

