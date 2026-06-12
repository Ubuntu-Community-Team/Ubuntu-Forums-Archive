---
title: "antivirus killed my penguin"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by neweb00 on 2010-03-10
hi i recently ran an antivirus for the first time it quarintined a number of items but when i restarted  the clock was missing and i could not access net or any folders. apps and free software centre still work and connect but i cannot access folders to move files back to destinations . is there an app that can scan my registery and download missing files? im a noob this this linux

/home/user/.ieauthority
could not update ieauthority
and
oafiid:gnome.clockapplet missing are the errors i get
thanks

---

### Post by Rex Bouwense on 2010-03-10
What AV program did you run?  Linux/Ubuntu is generally not subject to virus and cannot be infected unless you want to be infected (you have to give your permission to make changes to your system).

---

### Post by NightwishFan on 2010-03-10
Just reinstall the gnome panel applets package. I would advise you do not run antivirus as root or on anything but suspicious files. A false positive could do some damage. Antivirus is not yet needed for Linux-only systems.
```
sudo apt-get install gnome-applets gnome-applets-data
```

You will be lucky if that is the extent of the damage though it might not be related to the antivirus at all.

---

### Post by 2hot6ft2 on 2010-03-10
In ubuntu only run anti virus on your home folder which includes everything in your home folder including the desktop, or on specific files and folders that are not in the file system, not the root "/" of the file system because it will report some of the system files as suspicious. If you can't restore the files from quarantine then you will most likely have to reinstall and consider it a lesson learned.
But you can try the other solutions offered first.

There is no registry like in windows. The closest thing would probably be "gconf-editor" which you can open by pressing Alt+F1 and typing or pasting it in without the quotes or by using it in a terminal. It's a lot easier to understand than the windows registry.
> **neweb00 said:**
> 
/home/user/.ieauthority
could not update ieauthority
and
oafiid:gnome.clockapplet missing are the errors i get
thanks
Is this a WUBI Install?
That means is it installed in windows like an app where you put the disc in while running windows?

Since I don't have any "/home/user/.ieauthority" and I suspect that stands for InternetExplorerAuthority.
Mine is not a WUBI install so I have no Internet Explorer since that's a windows web browser.

---

### Post by presence1960 on 2010-03-10
Read this & forget about how things are in Windows: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Another good read to reinforce Linux is nothing like windows: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

BTW welcome to the community. If you stick around you will not only learn linux but probably a whole lot about computing in general. This is the best community!

---

### Post by myemptysoul on 2010-03-10
well the only way linux could possibly get a "virus" is for a person to create a dos underlayer then send you the virus attatched to a program you downloaded and when you gave that program the permission to install itself and run that gave the virus permission to install and run.  download and learn how to run OPENLDAP.  this is a decent program which makes linux "registry" see-able and able to manipulate.  [http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/) is where i learned how to run OPENLDAP and configure it.  Good Luck

---

