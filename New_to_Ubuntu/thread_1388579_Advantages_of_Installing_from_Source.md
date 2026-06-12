---
title: "Advantages of Installing from Source"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by LWhitson2 on 2010-01-23
Ok, I am really new to the Linux environment and I am curious about this building and installing from source code.  Is there an advantage or disadvantage to installing a program from source?  Also, what is the difference in installing something from the repository versus installing an application in a folder, such as Firefox or Eclipse?

Thanks,
Bryce

---

### Post by MelDJ on 2010-01-23
installing from the repo's means you get a trustworthy and safe package. and its also easier
installing from source lets  you configure the installation and programs like firefox might work faster (i think)

---

### Post by sp0nge on 2010-01-23
Most of the time, installing via apt is perfectly fine. The main advantage I see to installing software from source is that one might find newer versions of the software at the vendor's website which aren't available in the repos.

---

### Post by Paddy Landau on 2010-01-23
Unless you're a super-geek, wanting to spend time with errors and problems, just install from the repositories. As the previous poster said, it's easy.

In the rare case where the package you want isn't on the repository, download the DEB package and install that. Nice and easy.

---

### Post by JKyleOKC on 2010-01-23
> **LWhitson2 said:**
> Ok, I am really new to the Linux environment and I am curious about this building and installing from source code.  Is there an advantage or disadvantage to installing a program from source?  Also, what is the difference in installing something from the repository versus installing an application in a folder, such as Firefox or Eclipse?
Installing from source is the old, traditional way of doing things. However today's distributions often contain unique tweaks that can make a compiled-from-source program fail to do what one expected, and in addition the program will quite often have dependencies on various library files that are not yet on your system, making the compile fail until you've satisfied all of its needs.

Packages in the repositories have been tuned to work well on the specific distribution to which the repository applies; the "sources list" which provides the repository address tells distribution details. In addition, the "package" concept includes information about any dependencies, and the package manager (apt, aptitude, synaptic, add-remove, etc.) will automatically grab the needed files so that you don't come up missing one or two (although sometimes a conflict may prevent this).

Thus the major difference, these days, is that the repository offers a strong reassurance that the program will "just work," while compiling from source is more of a gamble. On the other hand, compiling from source lets you modify the program to meet any special need you might have, and usually provides assurance that the program hasn't been hacked somewhere along the way (however that's not a strong reassurance unless you're quite familiar with source code and able to detect such hacks by examining it).

Using packages downloaded through a browser or FTP from sites other than the official repositories or PPAs can be downright risky, since you don't have any assurance of security issues. Even manufacturer's sites have been known to unknowingly contain modified packages, so the risk is always present. Fortunately word gets around rapidly about really dangerous sites, so asking here before doing such a download is a good idea!

Welcome to the community!

---

### Post by lovinglinux on 2010-01-23
Unless you want an application not available in other format other than source code, or if you want to enable some features that are disable in the official repositories version, or if you want to optimize the application for your machine, then you would be better with a regular installation.

---

### Post by no2498 on 2010-01-23
from what ive seen you need to jump through hoops to get rid of the source's
reposes you can you just un install

---

### Post by Paddy Landau on 2010-01-24
> **no2498 said:**
> from what ive seen you need to jump through hoops to get rid of the source's
reposes you can you just un install
That's correct. If you install through the repository, or using a DEB download if not available in the repository, it's really easy to uninstall using Synaptic.

Otherwise, you need to know where all the files are stored in order to delete them.

---

### Post by PenguinInside on 2010-01-24
Installing from apt gives you these advantages:

[LIST]
[*]You can find out which files are associated with a given package.
[*]For a given file, you can find out which package it's associated with.
[*]You can remove all files associated with a given package, even if they're spread out over multiple directories.
[*]You can use a GUI to make things easier and get a screenshot before you install.
[*]You can know which packages are dependent on a given package
[*]You can know which packages a given package depends on
[/LIST]

Generally, 
[LIST]
[*]If the package is in the repositories, install from there
[*]If not, install from PPA (private repositories)
[*]If not, install from a .deb
[*]If not, install from source
[/LIST]

This is true even if you're an old Linux hand. You can install from apt immediately after downloading. If you compile, it'll take at least a minute or so, depending on the package. Why bother?

---

### Post by LWhitson2 on 2010-01-24
Thank you for everyone's input.  I hope that I can make this Linux thing work.  I have done quite a bit with my Windows Network so far (Active Directory, Network Shares, etc.) and I hope that I can do the same on the Linux side.  This is a huge undertaking for me, that is for sure.  Over the next few months you will probably see a lot of questions from me as I move forward.

---

