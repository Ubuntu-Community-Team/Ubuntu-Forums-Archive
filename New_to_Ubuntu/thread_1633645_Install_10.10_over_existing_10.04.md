---
title: "Install 10.10 over existing 10.04"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by johnfarrow on 2010-11-29
[SIZE=3]I currently have a 100 gb drive in laptop with....
   
   a.  a 44.5 gb partition on sda1 (fat32) for win xp
   b.  a 48.1 gb partition on sda5 (ext4)  for ubuntu 10.04
   c.  a 2.1   gb  partition on sda6 (swap) for 10.04 swap
   d.  a 5.3   gb partition on  sda3 (fat32) for reinstalling XP

I want to install 10.10 over the existing 10.04 and keep the win xp partition.
I plan on upgrading xp to win 7.

Which install option should I use?  And then?

Any and all advice appreciated.

John Farrow 
[/SIZE]

---

### Post by libssd on 2010-11-29
Use the manual partitioning option; install 10.10 in the same partition as 10.04. Reformat the partition with filesystem of your choice (e.g. ext4), set / as mount point, and change nothing else. You will lose all your existing data, of course, unless you have backed it up. I tried installing without re-formatting once, and had issues...

All should go well... but it would be prudent to make a backup first. :p

The best tip I have picked up in the past year is that you can copy your browser preferences to another disk, and then restore everything after a new OS install.

**Firefox**: [http://support.mozilla.com/en-US/kb/profiles](http://support.mozilla.com/en-US/kb/profiles)
**Chrome**: [http://www.google.com/support/forum/p/Chrome/thread?tid=6a3d820ca818336b&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=6a3d820ca818336b&hl=en)

---

### Post by matthewbpt on 2010-11-29
I would recommend upgrading your Ubuntu 10.04 to 10.10 if you have a good internet connection. Just press Alt+F2 and type ```
update-manager -d
```
Then you should see an option appear to upgrade to 10.10. I did this with no problems, much easier than making a whole new installation and you get to keep all your settings.

---

### Post by libssd on 2010-11-29
Fresh install of a new release vs update from an existing installation is one of those perennial questions. I haven't seen any horror stories for updating 10.04 to 10.10, but I have seen some for previous updates. If you choose update over upgrade, make sure that **ALL** available updates to 10.04 have been applied before attempting to update to 10.10.

Six of one; half a dozen of the other.

---

