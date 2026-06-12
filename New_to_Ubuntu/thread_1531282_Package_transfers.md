---
title: "Package transfers"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by K5-CJ5 on 2010-07-14
I am new to Linux but loved it right away so I decided to install on my Kids computer that has no Internet connectivity.  I want to download some software such as the primary education bundle for Ubuntu on my Internet connected desktop, no problem.  Is there a way to download software to a usb, or cd drive from the Internet connected computer so I can install on my non connected desktop?  I can only download 5gb per month, which I go over, and would like to save the software on cd or usb to share on multiple Ubuntu machines.  Is this possible??

Thanks

---

### Post by Zeike on 2010-07-14
You can download ubuntu packages at: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Double clicking them should launch the installer.

---

### Post by belkinsa on 2010-07-14
Don't forget mark this "Solved"

---

### Post by TCHebb on 2010-07-14
You can install the dpkg-repack package on your main machine, then use the command
```
sudo dpkg-repack <package name>
```to repack the installed package <package name> into a .deb file in the current directory. You can then transfer this file to other computers using a CD or USB Flash Drive.

---

### Post by K5-CJ5 on 2010-07-14
Thanks!! Problem solved... If I do this will it remove the program from my main machine?

---

### Post by TCHebb on 2010-07-14
No. dpkg-repack won't uninstall the package. If you want to remove the package from your system, you can use
```
sudo apt-get remove <package name>
```
This won't remove the .deb file you have created.

---

### Post by K5-CJ5 on 2010-07-15
OK, So I repacked the files, etc and then had to do the same for many others that were dependent....So that is not the way to go...Is there a way do directly download the packages to a folder, or usb or CD, so I can then install them from the usb or CD instead of over internet?  I know there has to be a way to download software to a location of your choice to install on a different machine.

---

