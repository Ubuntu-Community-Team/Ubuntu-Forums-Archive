---
title: "Install Rakarrack from tarball, for absolute beginner."
date: 2010-12-08
forum: New to Ubuntu
---

### Post by ingybingy on 2010-12-08
Hi there! Just started using Desktop Ubuntu 10.10, love it! But REALLY new to this. How do I get Rakarrack to install from a tarball? Or anything elese for that matter!

Thanks!:P

---

### Post by TeoBigusGeekus on 2010-12-08
Bookmark [this]("http://www.psychocats.net/ubuntu/installingsoftware") page.

---

### Post by cchhrriiss121212 on 2010-12-08
I would avoid installing things that way. Get it from a PPA instead:
[https://launchpad.net/~autostatic/+archive/ppa]("https://launchpad.net/%7Eautostatic/+archive/ppa")

---

### Post by transmogrifox on 2010-12-08
> **cchhrriiss121212 said:**
> I would avoid installing things that way. Get it from a PPA instead:
[https://launchpad.net/~autostatic/+archive/ppa]("https://launchpad.net/%7Eautostatic/+archive/ppa")

I agree with this.  Take some time to learn about Ubuntu's package management system and how software installation is handled on GNU/Linux in general.

If you are a windows user, you think in terms of downloading an exe or putting a CD in the drive, double click it on your desktop and go through an install wizard.  

For GNU/Linux (Ubuntu, for example) there is a package management system that contains information about software collections called "repositories".  For example, if you want to install Rakarrack, just open Synaptic Package Manager, or the Ubuntu software manager, and search 'rakarrack'.  If the default sources have a rakarrack package, then you just check it and select apply.  It will download the software and install it.  Really easy. (by the way, Ubuntu 10.10 does have Rakarrack, so you don't need to go any further from that unless you want some of the features added in a more recent release).

Sometimes the default repositories don't have the program you're looking for, or the program version is older than the version you want.  Then the next place to look are the PPA's.  PPA's are repositories that users have created.  Usually they are maintained by users who have made special bug fixes or modifications, or they simply keep an up-to-date version.

Then if you can't find it in the PPA's or any repositories, then you may want to download a .deb package for Ubuntu 10.10.  This would be the Linux counterpart of the Microsoft .exe installer (except on Ubuntu the package manager handles unpacking and installing the contents).

Finally, if you can't get the package in your distribution, or can't download a .deb package compatible with your system from somewhere -- or if you just want the educational experience -- then you would download source code and compile it.

Note the above is just help for a newbie to Ubuntu.  More experienced users have many other reasons I didn't mention for building packages from source (I have a few programs I like to build from source, myself).  I don't recommend starting there.

EDIT:  I took a look at the link offered by TeoBigusGeekus.  That says it all.  Very good link for newbies :D

---

