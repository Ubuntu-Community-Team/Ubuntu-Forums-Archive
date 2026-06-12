---
title: "errors"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by chris_baller on 2009-02-16
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is what is says when trying to update please help brand new just starting to read ubuntu manual now.

---

### Post by chris_baller on 2009-02-16
i guess i wasn't clear cause i couldn't find what i was looking for there on that link.  i've installed ubuntu over a wiped clean maxtor hard drive it runs good but now when i try to update through update manager i get this message    "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

If anybody can help me to fix this problem so i can update all the security and extra features.   On a side note could i still add windows to this i have partitioned the drive so i have 80g on 1 and 40g on the other.(or should i have installed windows first then ubuntu?)

Another error i get is when i check in the update manager this is what it says.   "Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

Please help this nubi understand i hate windows i need this to work

---

### Post by chris_baller on 2009-02-16
sorry but can anyone help my situation or maybe want to help

---

### Post by overdrank on 2009-02-16
HI and welcome, I have moved your post to its own thread so not to highjack anyone else.
Have you tried running that command in the terminal, the terminal is located under applications, accessories.
```
sudo dpkg --configure -a
``` 
As for the other error you may wish to remove the cd from your sources list. Under system, administration, software sources. Then you can remove the cd from the list.

---

