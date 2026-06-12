---
title: "Home Directory out of space"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by maidenschmidt on 2009-06-03
2week old install of 9.04.  Home directory is full.  is the a way to resize it?  i have a windows background and took all defaults during setup.  i assumed, incorrectly, that i could just grow my home directory kinda like my documents in windows.  Home directory is 10 gigs,and full, and hard drive is 160 gigs.  Are there
any tools to increased the size at all?  i would hate to reinstall when everything is setup just the way i like it. Had a issue logging in last night, but was able to free enough space to get the GUI working. Thanks for any help on this.

---

### Post by Celauran on 2009-06-03
You could boot from a LiveCD and use gparted to resize your partitions.

---

### Post by maidenschmidt on 2009-06-03
Awesome, i will do that.  Does it have to be from live CD or can it be ran from with in the OS? Also, are there any other factors i need to take into account when resizing?  Maybe damage to other drirectories that need X amount of space?

---

### Post by Celauran on 2009-06-03
It needs to be done via LiveCD because you cannot alter mounted partitions. Beyond that, I can't really comment. I don't know what your partition table looks like right now. Any partition with a bunch of extra space should be safe to resize, though if it's a Windows partition, you may want to defrag first.

---

### Post by maidenschmidt on 2009-06-03
Well i certainly appreciate the help.  this is on my New EEE 1000HE netbook with no windows installed.  Thanks again, sounds easy enough.

---

