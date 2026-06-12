---
title: "SCANNER UTILITY 2 Help"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-10-23
HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-setup requires GUI support (try running with --qt3). Also, try using interactive (-i) mode.

What does this  mean? I'm using SCANNER UTILITY. NOT xsane. It was working but every now and then I get an error message that says "invalid arguement"

does anyone have a solution you can help out with? I need this scanner asap  for a job!

---

### Post by sandyd on 2009-10-23
> **289531.EXE said:**
> HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-setup requires GUI support (try running with --qt3). Also, try using interactive (-i) mode.

What does this  mean? I'm using SCANNER UTILITY. NOT xsane. It was working but every now and then I get an error message that says "invalid arguement"

does anyone have a solution you can help out with? I need this scanner asap  for a job!
got kde installed?
if you don't, install the libqt4 libraries.

---

### Post by 289531.EXE on 2009-10-23
> **carlee said:**
> got kde installed?
if you don't, install the libqt4 libraries.

Whats kde? How do I find out and how do I install that library?

---

### Post by sandyd on 2009-10-23
> **289531.EXE said:**
> Whats kde? How do I find out and how do I install that library?
sudo apt-get install libqt4*
KDE stands for K Desktop Environment. 
Its a different GUI that has different libraries.

---

### Post by 289531.EXE on 2009-10-23
this is what i got

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt4
recluse@289531:~$

---

### Post by diesch on 2009-10-23
Install hplip-gui

---

### Post by 289531.EXE on 2009-10-23
I did and i still have the same problem

---

### Post by diesch on 2009-10-23
You don't need to install libqt4 after that, but hp-setup should run.

If not please run

```
sudo python -v $(which hp-setup) 2> hp-setup.log
```

and attach the file  hp-setup.log

---

### Post by 289531.EXE on 2009-10-24
it didn't do anything

---

### Post by cguy on 2009-10-25
> **289531.EXE said:**
> this is what i got

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt4
recluse@289531:~$

It's because you wrote
sudo apt-get install libqt4

and not
sudo apt-get install libqt4*

There's a an easier way, though: System > Administration > Synaptic Package Manager and search there for packages that contain "libqt4" in their names

---

### Post by 289531.EXE on 2009-10-26
i did itin the terminal and got this message 


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-ruby1.8: Conflicts: libqt0-ruby1.8 but 4:3.5.10-1ubuntu3 is to be installed
E: Broken packages

---

