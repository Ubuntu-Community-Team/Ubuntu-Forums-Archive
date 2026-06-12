---
title: "Virtual Box setup...can I do this?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by chromedome on 2010-03-04
Hi, there...silly question about VirtualBox.

I'm running Jaunty on my old Dell, and I have a completely separate, bootable XP filesystem on a secondary hard drive.  

What I'd like to do is use VB to run the XP system without the PITA of rebooting.  Can that be done?  How would I set it up?

---

### Post by sandyd on 2010-03-04
> **chromedome said:**
> Hi, there...silly question about VirtualBox.

I'm running Jaunty on my old Dell, and I have a completely separate, bootable XP filesystem on a secondary hard drive.  

What I'd like to do is use VB to run the XP system without the PITA of rebooting.  Can that be done?  How would I set it up?
since most people would want to have usb support, youll need to add the virtualbox repos.
Your using jaunty, so add this repository
```

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```

run
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-3.1

```
Run virtualbox, register, and click the "new" button

---

### Post by X1R1 on 2010-03-04
Good question! I would like to know this also.

---

### Post by anewguy on 2010-03-04
It's been a LONG time since I set something up using another partition with Windows already installed, but I imagine the steps are pretty similar.  Look in the included help with VirtualBox - there at least used to be an extended section on more advanced things, like using another partition with Windows already on it.  I would think selecting a partition on another drive would not be a problem.  The commands all fall under command-line based vboxmanage statements.

Good luck!

Dave ;)

---

### Post by Sir Jasper on 2010-03-04
Hi carlee and all,

Would the amount of RAM the ¨old¨ Dell has be of likely importance?

My regards

---

### Post by sandyd on 2010-03-04
> **Sir Jasper said:**
> Hi carlee and all,

Would the amount of RAM the ¨old¨ Dell has be of likely importance?

My regards
buddy, I used to run winxp in a virtualbox on a 512mb machine.
virtualbox complained, but I overrode its complaints, and it all worked fine. (the swap file was on a RAID 1. setup, so it was still....... kinda ok speed....)

---

