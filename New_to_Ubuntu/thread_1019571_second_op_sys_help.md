---
title: "second op sys help"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by budf on 2008-12-23
hey;  I have a second hard drive that I am trying to install ubuntu on.  I get the install process started and it seems like it wants to wipe out vista on the first drive rather than going onto the second drive.  help.

---

### Post by hyper_ch on 2008-12-23
can you post a screenshot?

---

### Post by halitech on 2008-12-23
are you doing a guided install or manual for the partitioning?

---

### Post by northern lights on 2008-12-23
Rather than picking the "guided install", which will use the entire harddrive and/or first drive, choose "manual install". Set up two or three partitions on the second hdd, one for the rootfilesystem, a swap partition (approx. 1 to 2 times the size of your physical memory or RAM) and an optional /home. I'd keep /home separate.

---

### Post by budf on 2008-12-23
Hey;  am a newbie so please talk slow and loud.  I tried the guided install.  please elaborate on the partitions.  thanks

---

### Post by northern lights on 2008-12-23
The manual install allows you to keep the Windows install alive and pick the place of install for Ubuntu yourself.

The downside is you have to set up partitions on your own. It's not that tough though, especially if you've done similar under Windows.

In Windows, virtual memory (space on the harddrive used for memory once the RAM is full) is kept in a file called pagefile.sys. In GNU/Linux it's a separate partition called SWAP. As a rule of thumb, make SWAP 1 to 2 times the size of your RAM.

Only two partitons, the main one and SWAP are essential. If you opt for a separate /home though it'd be much easier to reinstall in case you bork your system, cause tou don't have to backup documents and the like and can keep some configuration files also.

In Linux, the user generally just works in /home, which is somewhat similar to "My documents" in Windows. Somewhat.

The system partition is called root and denoted by a slash only (/). It needs to be bootable.

Both / and /home should be ext3, you make a partition SWAP by choosing SWAP under filesystem, rather than ext3.

---

### Post by budf on 2008-12-23
Hey northern lights;  I am from northern ontario originally and so miss the awesome display.  thanks for the info.  am not sure I understand some of it but am going to try.

---

