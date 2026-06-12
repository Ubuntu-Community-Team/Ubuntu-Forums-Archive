---
title: "compiz not working with sis graphics! HELP!"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Crazyatvspaz on 2010-06-28
i recently couldn't get compiz working on my net book. figured id giv my laptop a try....same problems.


zach@zach-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: glxinfo not installed 

Would you like to know more? (Y/n) Y

 The program glxinfo is needed to perform a number of crucial tests. 

 You need to install the package mesa-utils
 Type e.g. sudo apt-get install mesa-utils to install it. 

zach@zach-laptop:~$ sudo apt-get install mesa-utils
[sudo] password for zach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 50.4kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe mesa-utils 7.7.1-1ubuntu3 [50.4kB]
Fetched 50.4kB in 5s (8,736B/s)     
Selecting previously deselected package mesa-utils.
(Reading database ... 152277 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_7.7.1-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (7.7.1-1ubuntu3) ...



ive googled and researeched and i cant find any answers. Sis web site is a joke. please i want compiz!

---

### Post by Python Jedi on 2010-06-28
I don't see any problems with the install readout. What is the problem you are having?  Does compiz run?  What is marked when you go into System>Prefrences>Appearence>Visual effects?  One thing I do notice is that my computer doesn't have compiz-check, nor is it in the repositories. Where did you get it, so I can try it?

---

