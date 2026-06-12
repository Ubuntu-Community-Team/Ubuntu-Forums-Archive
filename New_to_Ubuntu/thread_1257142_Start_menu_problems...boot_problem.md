---
title: "Start menu problems...boot problem"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by OllieGab on 2009-09-03
Installed Ubuntu 9.04 from scratch. However, the boot stops fairly quickly, giving some "stange" explanation about not being able to find files needed...

If I ESC during the very first seconds of start up I get into a menu giving me a few options to what I want to boot up. The first one - and the one that is starting by default and is giving me grief - is called:

Ubuntu 9.04, kernel 2.6.28-15-generic

If I instead chose the 3rd choice; 

Ubuntu 9.04, kernel 2.6.28-11-generic

the machine starts without any problems.

Firstly, why? Surely the install should detect what "is needed" to start the computer?

Secondly, could it just be a case of commenting out the first two options in the menu.lst file? Would it then start with the working option without me having to tell it to?

Cheers from Ollie

---

### Post by ks07 on 2009-09-03
> **OllieGab said:**
> Installed Ubuntu 9.04 from scratch. However, the boot stops fairly quickly, giving some "stange" explanation about not being able to find files needed...

If I ESC during the very first seconds of start up I get into a menu giving me a few options to what I want to boot up. The first one - and the one that is starting by default and is giving me grief - is called:

Ubuntu 9.04, kernel 2.6.28-15-generic

If I instead chose the 3rd choice; 

Ubuntu 9.04, kernel 2.6.28-11-generic

the machine starts without any problems.

Firstly, why? Surely the install should detect what "is needed" to start the computer?

Secondly, could it just be a case of commenting out the first two options in the menu.lst file? Would it then start with the working option without me having to tell it to?

Cheers from Ollie
It may be that something in the newer kernel doesn't work well for your system. A quick **workaround** would be to quickly comment it out in your menu.lst. Sadly, I don't know how to fix it.

---

### Post by LewRockwell on 2009-09-03
it is probable/possible that your updating process(evidenced by having the newer kernel on your machine) may not have totally completed successfully

boot up with the older kernel and then use Synaptic to install kernel "Ubuntu 9.04, kernel 2.6.28-14-generic" if it isn't already on your machine

once you've installed it and booted to it successfully then you might need to uninstall and reinstall "Ubuntu 9.04, kernel 2.6.28-15-generic" to see if that cures your difficulties

you can also check for installed kernels:

[http://ubuntuforums.org/showthread.php?t=1185895](http://ubuntuforums.org/showthread.php?t=1185895)

.

---

### Post by OllieGab on 2009-09-03
Commenting out the first two options in the menu.lst file works fine!
I will look into the kernel upgrade as well, but as I am fairly new to Linux all tha kernel malarkey scares me a bit!:p

Cheers!

---

