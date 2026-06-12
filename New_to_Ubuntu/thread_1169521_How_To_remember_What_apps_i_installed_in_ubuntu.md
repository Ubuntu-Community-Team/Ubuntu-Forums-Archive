---
title: "How To remember What apps i installed in ubuntu?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-25
I am going to give my HDD for replacement and so the linux in it will also be deleted,I have one problem in it.I dont want to search all the apps i installed again and install them from begening.So is there any way to mark the softwares i have now and save them so that i can install all again.(i have backed up all data in /var/cache/apt/archives)

---

### Post by michy99 on 2009-05-25
Open Synaptic Package Manager. Click on Installed. (If you don't see Installed in the left panel, click Sections in the bottom left panel.) This will show you all the packages you have installed using the package manager (Synaptic, Add/remove, apt-get). Choose File->Save Marks As. This will  save a file which shows what packages are installed. After the new install, open Synaptic, File->Read Marks, and read in the file you saved. Then you can apply changes and everything should install.

This does not include anything you installed without the package manager, for example by compiling from source.

---

### Post by Didius Falco on 2009-05-25
Hi,

Here are two ideas for you:

1. Download "RemasterSys" (there is a link in my signature) and use it to make a bootable CD/DVD of your entire install. You can use it to restore everything at once.

2. Download "aptoncd" - It's available via Synaptic. It will make a CD/DVD that you can add to Software Sources that is a portable home repository. You can reinstall every package that is on your PC.

Both are easy to use. Aptoncd won't install the packages, but it makes it easy for you to do so without using up bandwidth.

RemasterSys is a bootable, installable Live CD that you can use to restore your system to the same state it was in when you created the backup.

Regards,

Didius

---

### Post by CatKiller on 2009-05-25
You can use 

```
dpkg &#8722;&#8722;get&#8722;selections > ~/Desktop/installed-programs
```to create a list on your Desktop of the packages you have installed. When you've re-installed Ubuntu on your new hard drive, copy that file to the Desktop of the new install. Then use

```
dpkg &#8722;&#8722;set&#8722;selections <  ~/Desktop/installed-programs
```to mark for installation all the packages in that file. Then use

```
sudo apt-get dselect-upgrade
```to install all of the packages that have been marked for installation.

---

### Post by mirons on 2009-05-25
Some time ago I made a little python script to print on a file all packages I have installes. The code is below
```

#!/usr/bin/python
# -*- coding: utf-8 -*-
# the line above must be deleted if you're not using utf-8 as coding, but it's default in ubuntu

import sys
from getopt import gnu_getopt as getopt
from debian_bundle.deb822 import Packages

options = getopt(sys.argv[1:],"o:",["output="])
    
# Deal with options
for option, value in options[0]:
    if option == '-o':
        sys.stdout = open(value,'w')

for pack in Packages.iter_paragraphs(file('/var/lib/dpkg/status')):
    
    if pack['status'].split(" ")[0] != 'install':
        continue
    else:
        print pack['package']


```

You have to paste it in a new text file make it executable with command ' chmod 755 <filename> ' and execute with './filename -o outputfile'
I don't know if it's exactly what you want but I had it, and think it fit your problem.

---

