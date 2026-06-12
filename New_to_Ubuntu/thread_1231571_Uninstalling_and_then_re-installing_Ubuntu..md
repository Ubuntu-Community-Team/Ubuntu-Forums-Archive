---
title: "Uninstalling and then re-installing Ubuntu."
date: 2009-08-04
forum: New to Ubuntu
---

### Post by apprentice789 on 2009-08-04
During the installation of Ubuntu something when wrong and I want to uninstall it from my computer and reinstall it correctly. I uninstalled it from the add/remove in Window Vista but Ubuntu still shows up at the beginning of the start-up and still able to boot up when I restart my computer. How do I completely uninstall Ubuntu? I want to be able to reinstall a clean copy of Ubuntu on my computer. I want to have a dual boot with the option of booting to Window Vista or Ubuntu. I also want to have Window Vista first in the booting hierarchy and Ubuntu second at this time until I completely change over to Ubuntu exclusively. I will change the hierarchy of the boot then with Ubuntu first on the hierarchy. I'm a complete novice so I don't understand much about partitiions and such.

---

### Post by bodhi.zazen on 2009-08-04
Sounds like you installed using wubi.

See :

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Your other option is to install Ubuntu the "Standard" way by partitioning your hard drive and installing Ubuntu into it's own partition.

I would do the second and make a shared (ntfs) data partition.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by lkraemer on 2009-08-04
If you are going to be making a "Dual Boot" system, here is the
BEST INFORMATION available.

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

lkraemer

---

### Post by apprentice789 on 2009-08-05
I download the ISO of Ubuntu from the website _[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)_ and burn it to a CD.  On the CD when I burned it has a file in there that says Wubi.  Can I use that CD to do what you are saying about installing Ubuntu on a standard partition?  Explain what I should do and how to get a copy of the CD so I do the standard partition option.

---

### Post by bodhi.zazen on 2009-08-05
To perform a standard install, reboot your computer. You may need to change your bios so that the Cd boots before the hard drive.

---

### Post by apprentice789 on 2009-08-08
How do I get my laptop which is running Windows Vista Home Premiun to boot first from the CD before the hard disk?  I want to delete Ubuntu from the the boot listing at the beginning that allows you to choose which operating system to boot from.  I used the add/remove in Windows Vista to unisntall Ubuntu already but Ubuntu is still showing up at the beginning when I reboot.  I just want to completely uninstall Ubuntu.

---

### Post by bodhi.zazen on 2009-08-08
> **apprentice789 said:**
> How do I get my laptop which is running Windows Vista Home Premiun to boot first from the CD before the hard disk?  I want to delete Ubuntu from the the boot listing at the beginning that allows you to choose which operating system to boot from.  I used the add/remove in Windows Vista to unisntall Ubuntu already but Ubuntu is still showing up at the beginning when I reboot.  I just want to completely uninstall Ubuntu.

In post #2 I gave you a link that describes how to uninstall Ubuntu (wubi).

Or did you do a standard install and want to replace grub ?

---

### Post by apprentice789 on 2009-08-08
I did use the installation of Ubuntu using Wubi and I got the download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)[]("http://www.ubuntu.com/getubuntu/download").  I did go to the link in post #2 and tried to follow instruction there.  Some of the steps I couldn't do because I didn't have those options that you describe.  I even downloaded Easy BCD but that gives you the option of uninstalling Ubuntu inside Windows Vista.  I did that already.  I want to get rid of Ubuntu completely because it shows up as a boot option alongside Window Vista at the beginning of the restart.  Nothing is showing up in the add/remove in Window Vista so there is nothing to uninstall.  Once I completely uninstall Ubuntu then I want to install Ubuntu in another partition on my hard disk.  Please tell me how to do that as well.

---

### Post by bodhi.zazen on 2009-08-10
Remove Ubuntu (Restore Windows): 
    [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Install Ubuntu : 

[GraphicalInstall - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GraphicalInstall") 

See also : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

