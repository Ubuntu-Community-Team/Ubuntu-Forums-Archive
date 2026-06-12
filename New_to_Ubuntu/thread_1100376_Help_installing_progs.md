---
title: "Help installing progs"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by dejay68 on 2009-03-19
I recently downloaded Avant Window Navigator 0.3.2 but dont know how to install it ! any help would be much appreciated.
ps: already have Avant Window Navigator 0.2.6 installed.

---

### Post by finer recliner on 2009-03-19
i assume that 0.2.6 was installed from the repositories (apt-get install avant-window-navigator), but you're looking to upgrade to the very latest. If 0.3.2 is not in the repositories, you'll have to compile it yourself from source. instructions on how to do this are here:

[http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource)

---

### Post by lovinglinux on 2009-03-19
> **finer recliner said:**
> i assume that 0.2.6 was installed from the repositories (apt-get install avant-window-navigator), but you're looking to upgrade to the very latest. If 0.3.2 is not in the repositories, you'll have to compile it yourself from source. instructions on how to do this are here:

[http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource)

Don't scare the OP :)

If want to install downloaded programs look for deb files. They are similar to Windows exe files, which means all you have to do to install is to double click on it. If you cannot find a deb file, but can find a tar, then you will probably have to compile from source.

I'm running Ubuntu for 6 months and I never compiled anything. Most of the time I was able to find a deb file.
Another easy option is to add a launchpad repository to your sources list

> 
From [http://d0od.blogspot.com/2009/02/avant-window-navigator-032-released.html](http://d0od.blogspot.com/2009/02/avant-window-navigator-032-released.html)

**To Install**

If you already have AWN installed, upgrading is easy. Either wait until your distro add's the updated packages to your repos - in which case you'll get an update notification in a few days/weeks. Or, if you're realllly impatient, you can upgrade manually.

add the following two lines to your software sources or equivalent. : -

deb [http://ppa.launchpad.net/awn-core/ppa/ubuntu](http://ppa.launchpad.net/awn-core/ppa/ubuntu) **intrepid** main
deb-src [http://ppa.launchpad.net/awn-core/ppa/ubuntu](http://ppa.launchpad.net/awn-core/ppa/ubuntu) **intrepid** main

Next add the key: -

In Ubuntu, open a Terminal and paste (CTRL + SHIFT + V)

    sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5FC1113B3009C37828E7EF1709266047CE9FDCA9

Please notice that this repository is for Intrepid.

---

### Post by SunnyRabbiera on 2009-03-19
Installing apps in Ubuntu is actually quite simple.
We use something called a repository, a central core of packages, this way you dont have to go to website a, website B or website c like in windows.
To use these repositories Ubuntu has two tools for you:
Add/remove which give you a base line of applications and Synaptic package manager that gives you every package.
Add/remove is easy to find, Synaptic can be found under system> administration> synaptic package manager.
For packages that are not in the repositories, its better to use the PPA Launchpad stuff.

---

