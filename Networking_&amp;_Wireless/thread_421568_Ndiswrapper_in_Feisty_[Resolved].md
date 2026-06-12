---
title: "Ndiswrapper in Feisty?? [Resolved]"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by ianb72 on 2007-04-24
How can I install ndiswrapper in Fiesty as I want to install my Linksys WUSB11v4 network adapter

cheers 
Ian

---

### Post by PartisanEntity on 2007-04-24
You will have to download it manually from packages.ubuntu.com as it was removed from the Feisty CD as far as I could make out.

---

### Post by ianb72 on 2007-04-24
How do I do that??

I tried

[HTML] sudo apt-get install ndiswrapper-common
and 
sudo apt-get install ndiswrapper[/HTML]

but I get

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
[/HTML]

Both times:confused:

---

### Post by PartisanEntity on 2007-04-24
I forgot to ask, are you connected using ethernet connection at the moment?

---

### Post by trubblemaker on 2007-04-24
```
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by ianb72 on 2007-04-24
> **PartisanEntity said:**
> I forgot to ask, are you connected using ethernet connection at the moment?

Yeah I am through my modem router on a wired connection.
But I am also running 2 Ubuntu PC's one with 7.04 and one with 6.06, but its the 7.04 I want to configure for the Linksys wireless network adapter.

---

### Post by ianb72 on 2007-04-24
> **trubblemaker said:**
> ```
sudo apt-get install ndiswrapper-utils-1.9
```

OK I tried that and I get this:

[HTML] ian@ian-desktop:~$ sudo apt-get install ndiswrapper-utils-1.9
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9
[/HTML]

I am connected to the internet as I am using the 7.04 PC now. :confused: 

Any ideas??

---

### Post by PartisanEntity on 2007-04-24
Try going to System > Administration > Synaptic Package Manager

Then click on Search and enter ndiswrapper.

See what you find and try to install it from there.

---

### Post by ianb72 on 2007-04-24
> **PartisanEntity said:**
> Try going to System > Administration > Synaptic Package Manager

Then click on Search and enter ndiswrapper.

See what you find and try to install it from there.

Tried that it cant find it!!!

---

### Post by ianb72 on 2007-04-24
sorted now

I updated the software sources then updated Synaptics and now It works when I type
[HTML]an@ian-desktop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 50.1kB of archives.
After unpacking 225kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com feisty/main ndiswrapper-common 1.38-1ubuntu1 [18.0kB]
Get: 2 http://gb.archive.ubuntu.com feisty/main ndiswrapper-utils-1.9 1.38-1ubuntu1 [32.1kB]
Fetched 50.1kB in 0s (253kB/s)           
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 88002 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
ian@ian-desktop:~$ 

 [/HTML] 

Thanks for your help
Sorry for being and idiot but I am new to Ubuntu after years of being on Windoze but I'm not going back to it, Ubuntu is way too cool as so fast

Ian

---

### Post by trubblemaker on 2007-04-24
I think everybody does that one once. No worries

---

