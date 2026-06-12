---
title: "HELP :-( Update manager, Package manager &amp; Ubuntu Software Center not working!"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by globalkk on 2010-12-05
I am new to ubuntu...and using Ubuntu 10.10

Recently my i encountered the following problems. It would be really helpful if some1 can help...

1.My Update Manager not working and is showing


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'





2. My Synaptics Package Manager is showing

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


3.Ubuntu Software center is not opening at all.....
Please somebody help me...

---

### Post by 73ckn797 on 2010-12-05
In Synaptic go to status and fix or remove any broken packages. Then open a terminal and enter ```
sudo apt-get clean
```.
See what happens after doing this.

---

### Post by owiknowi on 2010-12-05
Two thoughts:
1. Something went wrong during installation eg how did you install ubuntu (CD/DVD, netinstall, with or without automatic updates during installation?
In my personal(!) experience a fresh installation works best from (alternate)CD without network connection during installation.
2. Are the url's to the update repositories correct(?

---

### Post by globalkk on 2010-12-05
Hey THanx for Help 

I tried the sudo apt-get clean
and then agin tried to update by sudo apt-get update in terminal bt

still i get...

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by sikander3786 on 2010-12-05
Try with an older dpkg/status file.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

And then post the output of this one.

```
sudo apt-get update
```

---

### Post by globalkk on 2010-12-05
Still it is saying

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by arjunlalb on 2010-12-05
did u try to update the repository from terminal??

---

### Post by asanti on 2011-05-28
I found this, I tried it and it worked for me, although the error came back and I ran it again, so far so good.  I think the error may come back once there are more updates. Hope this will help you out.


While using the package manager or trying to install applications through Terminal, it is possible to get a nasty error which is something like this :

E:Encountered a section with no Package: header,

E:Problem with MergeList /var/lib/apt/lists /us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages,

E:The package lists or status file could not be parsed or opened.

This  will prevent from  installing or upgrading any application in  Ubuntu 11.04.  Fortunately, the fix is simple for this.

From the Terminal type the following commands :


sudo rm /var/lib/apt/lists/* -vf


This  will delete the older entries and download the latest ones after which the error should no longer be there.

sudo apt-get update

---

