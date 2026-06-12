---
title: "Input/output error E: Sub-process /usr/bin/dpkg returned an error code (2"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by ajeetraj on 2009-07-16
Hello everyone, 

I just installed new Jaunty on my old laptop Dell Latitude D600. everything seems to work apart from when I want to install something. I cannot install anything. Forget about installing something, I can't even get the updates. 

At the end I get the following error code: 

```
deepu@newleaf:~$ sudo apt-get install adobe-flashplugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  adobe-flashplugin
0 upgraded, 1 newly installed, 0 to remove and 152 not upgraded.
Need to get 3964kB of archives.
After this operation, 10.2MB of additional disk space will be used.
Get:1 http://archive.canonical.com jaunty/partner adobe-flashplugin 10.0.22.87-2jaunty1 [3964kB]
Fetched 3964kB in 10s (361kB/s)                                                                                                                             
Selecting previously deselected package adobe-flashplugin.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `perl-modules': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

this is what I got when i tried to get the adobe flash plugin for instance, but I get the same error for everything. 

Please some help me out here. 

Thanks! :)

---

### Post by ajeetraj on 2009-07-17
bump

---

### Post by Partyboi2 on 2009-07-17
Hi, open a terminal and try
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install adobe-flashplugin 
```
If that does not work then try reinstalling perl-modules.
```
sudo apt-get --reinstall install perl-modules
```

---

### Post by fraser_m on 2009-07-17
Open up a terminal, and run:
```
sudo dpkg --force-all -r perl-modules
```

---

