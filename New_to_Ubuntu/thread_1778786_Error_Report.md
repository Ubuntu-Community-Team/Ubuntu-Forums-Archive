---
title: "Error Report"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by cybermonkey on 2011-06-09
[LIST=1]
[/LIST]I'm new to Ubuntu. Recently installed 11.04 and now I keep getting the following error report about the Update Manager:

"E:Encountered a section with no Package:header,
 E:Problem with MergeList/var/lib/apt/lists/
ca.archive.ubuntu.com_ubuntu_dists_natty_main_binary_i386_Packages,
E:The Package lists or status file could not be parsed or opened."

If anyone knows what this means and what I need to do, it would be greatly appreciated.

---

### Post by wojox on 2011-06-09
This seems pretty popular the last few days.
Run these three commands in the Terminal Ctrl+Alt+T

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean all
sudo apt-get update 
```

---

### Post by cybermonkey on 2011-06-09
Thank you!  Worked!

---

