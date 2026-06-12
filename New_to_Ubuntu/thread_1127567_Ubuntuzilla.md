---
title: "Ubuntuzilla"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Rikumari on 2009-04-16
Hi there, i'm an ubuntu freshie, i don't really know how everything works yet.  I'm using Ubuntu 7.04, and would like to update firefox 3.  After searching through the internet, i found an application called ubuntuzilla, which is a gui installer for mozzilla packages such as firefox.  When i follow the instructions, after double clicking on the ubuntuzilla-4.6.1-0ubuntu1-i386.deb file i get an error saying "ERROR: Dependancy no satisfiable: libnotify-bin" (see attached screenshot). Could anyone tell me what this means, and ways to fix it? 

Thanks!

---

### Post by matrixblue on 2009-04-16
> **Rikumari said:**
> Hi there, i'm an ubuntu freshie, i don't really know how everything works yet.  I'm using Ubuntu 7.04, and would like to update firefox 3.  After searching through the internet, i found an application called ubuntuzilla, which is a gui installer for mozzilla packages such as firefox.  When i follow the instructions, after double clicking on the ubuntuzilla-4.6.1-0ubuntu1-i386.deb file i get an error saying "ERROR: Dependancy no satisfiable: libnotify-bin" (see attached screenshot). Could anyone tell me what this means, and ways to fix it? 

Thanks!

Look under system for the Synaptic Package Manager and search for libnotify-bin and install it.

---

### Post by James_Lochhead on 2009-04-16
A dependency is a package (program) that is required for another package to work. In this case you need libnotify-bin in order for Firefox to work.

I would recommend updating actually... we get new packages when Ubuntu is updated. Installing Firefox 3 and other new packages will be much easier with a newer version of Ubuntu.

I suggest going to 8.10 rather 9.04 though as 8.10 is now nice and stable. Newer releases of Ubuntu always have a few kinks at first.

---

### Post by Rikumari on 2009-04-16
I looked In the Synaptic Package Manager, and could only find libnotify1, installed version 0.4.3-1. Is it possible to download the libnotify-bin, and install it?

---

### Post by Rikumari on 2009-04-16
> **James_Lochhead said:**
> A dependency is a package (program) that is required for another package to work. In this case you need libnotify-bin in order for Firefox to work.

I would recommend updating actually... we get new packages when Ubuntu is updated. Installing Firefox 3 and other new packages will be much easier with a newer version of Ubuntu.

I suggest going to 8.10 rather 9.04 though as 8.10 is now nice and stable. Newer releases of Ubuntu always have a few kinks at first.
I am planning to get a later version of ubuntu, but i don't have a large download cap, so i have to find another way to get a distrobution copy.  On the ubuntu site, the free ubuntu distro is offline or something. I will ask around for someone with a copy though. thanks

---

### Post by matrixblue on 2009-04-16
You should use Ubuntu's Free Shipit service ([https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)), They will send you a copy for free. (Will take a few weeks though depending on your location).

---

### Post by por100pre1 on 2009-04-16
> **Rikumari said:**
> I am planning to get a later version of ubuntu, but i don't have a large download cap, so i have to find another way to get a distrobution copy.  On the ubuntu site, the free ubuntu distro is offline or something. I will ask around for someone with a copy though. thanks

You can use Shipit, as previously posted, or can check if there's an [Ubuntu LoCo Team]("http://ubuntuforums.org/forumdisplay.php?f=183") near your location. Maybe somebody near your location can send you a copy.

---

### Post by lhb1142 on 2009-04-16
:KS ShipIt is now reopened. I pre-ordered my disc today.

For whatever it's worth, to update Firefox, close everything out and open a terminal. Type < sudo firefox > (the words only, not the brackets) and the "dafault" Firefox will open.

Then go into < Help -> Check for Updates > (this is normally greyed out but it will be active here) and then click on it.

This will update your Firefox. Make sure you close the terminal BEFORE you close the Firefox.

The, when you next go into your "normal" Firefox, if you check < Help -> Mozilla Firefox > you will see that you have the latest version.

I hope this helps you. ):P

---

### Post by Rikumari on 2009-04-18
Thanks guys, and i will order one from ship it now that it has re opened. cheers

---

