---
title: "How to recover from removed networking packages"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by mountainshows on 2008-02-21
Hi,

I was attempting to get the size of my distribution down to the point where I could back it up onto a cdrom. In the process I removed a package called: dhcdbd. It appears that this has broken the ability to connect to my dhcp server and so I can no longer update over the network, oops.

I do have the kubuntu 7.10 cdrom that I made the original installation from, and I tried using apt-cdrom to add it to /etc/apt/sources.list. However, I am still getting error messages from apt-get regarding network access when I run apt-get install dhcdbd.

What is the correct way to install packages from cd in this case where I broke network access?

Thanks!

Ryan

---

### Post by pytheas22 on 2008-02-21
You should be able to get it off the CD.  Did you remember to update the repository list after adding the CD as a repository?  You might try using Synaptic instead of doing it from the command line (I'm not sure but I think Kubuntu has Synaptic).  Uncheck the network repositories, add your CD and make sure you press the reload button in the upper-left corner.

Otherwise you could download it from [http://packages.ubuntu.com/gutsy/dhcdbd](http://packages.ubuntu.com/gutsy/dhcdbd) and move it to your Ubuntu machine.  Of course, that will only work if the packages it depends on are still there.

---

### Post by blazercist on 2008-02-21
what do you need dhcp for?  set an ip address manually and reinstall the package...

---

### Post by mountainshows on 2008-02-21
This worked. Thanks! 

> what do you need dhcp for? set an ip address manually and reinstall the package...

---

