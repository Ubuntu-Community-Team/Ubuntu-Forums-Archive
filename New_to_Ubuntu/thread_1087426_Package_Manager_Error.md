---
title: "Package Manager Error"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by webbie180 on 2009-03-05
Pse help, have this error with package manager...

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_intrepid-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by swoody on 2009-03-05
Try this out:
```
sudo dpkg --clear-avail
sudo apt-get update
```

if that doesn't work, try:
```
sudo dpkg --configure -a
sudo apt-get update
```

If that still doesn't work, try this:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
This last code worked for the OP here: [http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)
But as with any 'rm' command with the 'force' option, you should always be careful. It seems that the directory that is removed is replaced when you run 'apt-get update' so there shouldn't be any harm :)

Let me know if you have any success with these :D

---

### Post by webbie180 on 2009-03-05
BINGO.......thanks alot..the last code with 'rm' works.

But when I tried to upgrade, this error shows

dpkg: parse error, in file `/var/lib/dpkg/status' near line 11180 package `gnome-games':
 MSDOS EOF (^Z) in field name `

even thou I have use synatic to correct the dependencies prob.

---

### Post by webbie180 on 2009-03-05
Solved by removing the status file.....

All back to normal now.

---

### Post by swoody on 2009-03-05
Great! Glad to hear everything is working for you again :)

---

