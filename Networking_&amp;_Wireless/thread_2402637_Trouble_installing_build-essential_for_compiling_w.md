---
title: "Trouble installing build-essential for compiling wifi drivers on 18.04"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by perceptron2 on 2018-10-02
Hi all -- 
Just installed Ubuntu 18.04 on a machine with no ethernet access. I have a TP-LINK Archer T4u wi-fi adapter I am trying to install, but I've had trouble. 

Instructions for installing the drivers say to run "sudo make" and then "sudo make install" from the directory of the drivers. However, I get an error that 'make' could not be found. The machine does not have internet access, so all of my attempts to install build-essential, which I have read contains 'make,' have failed. 

I'm in a real catch-22 here. How can I compile and install these wifi drivers without Internet access?

Thanks!

---

### Post by wildmanne39 on 2018-10-02
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by guiverc on 2018-10-02
If you look at [https://packages.ubuntu.com/bionic/build-essential](https://packages.ubuntu.com/bionic/build-essential)  (from the machine you're read this for example), it will show the package you need to download, plus any dependencies (the depends bits).  You download these onto a thumb-drive (floppy drive, tape drive), and use the old *sneaker-net* (ie. walk the tape/floppy/thumb-drive) to your machine, then mount the device, and install it locally.  You can install using `dpkg.  If you get any errors (more depends/dependencies), you'll have to go walk them across too.  `dpkg` requires all deps/depends to be installed to succeed (apt will get depends from the internet, but you can't use that!) so you'll have to install deps first, or install them all at once.

note:  the site ([https://packages.ubuntu.com](https://packages.ubuntu.com)) is useful for looking up deps (dependencies), and is not for downloading. You download from whatever site you use, for example if using the main site you can get from [http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)  (which contains multiple versions; you grab the version that `apt` or `apt-get` would grab, or the version listed in the packages.ubuntu.com page for your release of Ubuntu...   Be careful and grab the correct versions of each package (what `apt` tools do automatically) as you'll have problems if you try and use wrong ones.

---

### Post by chili555 on 2018-10-02
Do you still have the install DVD or USB  from which you installed Ubuntu? Which? DVD, we hope! All the needed packages are on it.

---

