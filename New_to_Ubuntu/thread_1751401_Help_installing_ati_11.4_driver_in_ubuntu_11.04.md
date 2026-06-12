---
title: "Help installing ati 11.4 driver in ubuntu 11.04"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by chromatica86 on 2011-05-06
I've downloaded the appropriate file from the ati site. When i choose to run it in the terminal, it tries to start but then quits. Anyone know why?
This is on a 64bit system with radeon hd3870.
I'm using the driver from the "additional drivers"(which was not installed while trying the other one) but am having not so good perfomance.

---

### Post by chromatica86 on 2011-05-07
Ok so now I've gotten a little further.
I've opened the terminal
cd ~
sudo sh ati-driver-installer-11-4-x86.x86_64.run
enter password
then it gives me this

ATI Catalyst(TM) Proprietary Driver 8.841
1) Install Driver 8.841 on X.Org 6.9 or later
2) Generate Distribution Specific Driver Package
Please choose the product to install, or Q to quit.  [1] 

Install aborted - cleaning up files
Removing temporary directory: fglrx-install.2EENab

I'm assuming this is where the gui window should be popping up, but it's not happening.
What am I doing wrong?

---

### Post by beew on 2011-05-07
Instead of downloading from ati can you just use Additional Drivers?

---

### Post by chromatica86 on 2011-05-07
> **beew said:**
> Instead of downloading from ati can you just use Additional Drivers?
That's what I'm using now, but it's outdated, and I was hoping to increase performance with a the newer driver.

---

### Post by chromatica86 on 2011-05-07
Well folks. I have gone back to 10.10.

---

### Post by deltacomp on 2011-05-07
Hello, I have use this tutorial in the past to install NVIDIA drivers. I think you can follow the same procedure, as long as you substitute your driver. Good luck. 

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=)

---

### Post by hittingray on 2011-05-22
It worked for me, when it asks for an option, press 1, and it should continue. Had no problems here.

---

