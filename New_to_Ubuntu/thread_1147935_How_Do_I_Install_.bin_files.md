---
title: "How Do I Install .bin files???"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by fslezak on 2009-05-03
Hello. I need to install a .bin file and I don't know how and where to install it. The .bin file is a Google Earth 5 installer.

Please Help Me!!!

---

### Post by lisati on 2009-05-03
From the terminal, go to the directory (ooops, read "folder": I've got Windows running on another machine) where you've stored the file, type in ```
chmod +X <filename>
./<filename>
``` (where "<filename>" is the name of the .bin file) and you should be in action.

---

### Post by fdrake on 2009-05-03
[see here]("http://www.linuxforums.org/forum/installation/46122-how-install-bin-file.html")

---

### Post by fslezak on 2009-05-03
Thanks a lot. It worked perfectly.

---

### Post by tjwoosta on 2009-05-03
ill help break it down a bit

1. first you give the .bin file executable permissions 
(this can be done two ways)

first way: 
locate the file in a file browser, right click and choose properties then choose the permissions tab and put a check mark in the box that says "allow executing file as a progream"

second way:
using the terminal navigate to the directory where the file is located and run this command
```
chmod +x filename.bin
```

2. now you execute the file
(this can also be done a couple different ways)

first way: 
double click on the file

second way: 
using the terminal navigate to the directory where the file is located and run this command
```
./filename.bin
```

EDIT: lol, sorry i took too long to type

---

### Post by kocmodpom on 2009-11-03
The file name I am trying to install is **OOPIC_Pro_2_0_2_eval_installer.bin**

I tried
```
chmod +x OOPIC_Pro_2_0_2_eval_installer.bin
```then
```
./OOPIC_Pro_2_0_2_eval_installer.bin
```the result?

> theimmortal@ubuntu:~/Desktop$ ./OOPIC-Installer.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6748/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory



So I tried downloading the .bin again and tried the previously suggested, -> properties -> check "allow executing as program"

Then when I double click I get 

> Could not display "/Pro_2_0_2_eval_installer.bin".
The file is of unknown type

WTF?

---

### Post by tjwoosta on 2009-11-05
In your first result the .bin was executing fine but your missing some dependencies. Its looking for shared system libraries and not finding them. You need to find whatever packages supply libm.so.6, libc.so.6, librt.so.1, and libpthread.so.0. I couldn't tell you what those packages are, but you could try searching for them in synaptic. Also they're probably listed in a readme file if one came with the .bin.

In your second result, it looks like your .bin is corrupted.

---

### Post by SunnyRabbiera on 2009-11-05
Or you might be able to find a .deb

---

