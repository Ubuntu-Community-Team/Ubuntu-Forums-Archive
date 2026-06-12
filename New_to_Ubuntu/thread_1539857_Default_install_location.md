---
title: "Default install location?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Someone uk on 2010-07-27
where do programmes go when they are installed by the ubuntu software centre, is there a default location for program files?

---

### Post by VH-BIL on 2010-07-27
It is organised.

The binary files go in
/usr/bin

Libraries (Like dll files in Windows) go in
/usr/lib

Icons go in
/usr/share/icons

pictures go in
/usr/share/pixmaps

etc...

Some programs (for example boxee) go in
/opt


You can right click on an installed application in synaptic package manager (it is just like the software center) and click on properties. If you click the Installed Files tab you will see what and where the files are installed.

---

### Post by typal on 2010-07-27
Try a "whereis [program name]" in a terminal. That will tell you where the files are located. Usually, it will be more than one spot. Check the guide [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/directories-file-systems.html") for a description of what goes in each folder. For instance,  /bin holds the binaries for programs.
Good Luck,
T

---

