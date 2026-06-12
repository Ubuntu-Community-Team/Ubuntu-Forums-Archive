---
title: "Kubuntu Installation + Partition Question"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-01-20
(see attached screenshot)
i want to install kubuntu and triple boot. i already have 4 primary partitions.  could i shrink the windows partition then expand the extended partition to the left to create a new partition for my kubuntu system?  any other suggestions for how i could go about this?  i want to maintain the same /home for kubuntu.  thanks for any and all help!

---

### Post by jimmy the saint on 2009-01-20
You don't need to do another install if all you want to do is have a KDE desktop in addtion to your Gnome desktop.  All you have to do is install the desktop.  When you hit the login screen, you would select KDE as the session.  Remember, with Linux, your desktop environment is just a shell.  You can have 10 different desktop environments with the same installation.  (I had a lot installed at one point to test them out.)

Here is a pretty good simple guide with some simple explanations as well.
[http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html](http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html)

---

### Post by Ben Page on 2009-01-20
I see you have one root ext3 partition, so it means you probably already have Linux-ish OS, jimmy is right, you can install KDE, Gnome, xfce ...environments, even kde 3 and KDE 4 on same Linux, so why would you install more than one "base" linux plus more shells. It would be risky to make so many changes to your partition table, you could loose data. There is a Windows utility called Partition Magic 8.0 - google it, it will allow you to do almost everything you want to your p.table and has very intuitive GUI.

---

