---
title: "SMB Questions"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-09
I have a SMB question. Right now I have a Iomega NAS.  When i first installed ubuntu it did not show up at all.  After reading several posts i probably downloaded and installed atleast 10 programs.  After that it works!  Basically i would like to know what I dont need so i can uninstall it.  So, what is needed to be installed to see my iomega nas? Thanks

---

### Post by anubhavrocks on 2010-11-09
Can you post the list of 10 packages that you have installed?

One tip is, you can look at the description of the package in Synaptic to make a decision yourself.

---

### Post by sully101 on 2010-11-09
You should be able to see a history of what you have installed in /var/log/apt/history.log

---

### Post by dFlyer on 2010-11-10
From the command line you can try sudo apt-get autoremove which will remove any unused packages.

---

