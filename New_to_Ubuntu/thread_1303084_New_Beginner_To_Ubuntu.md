---
title: "New Beginner To Ubuntu"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Ineed2know on 2009-10-27
](*,) I am strongly considering moving to Ubuntu from Windows XP Home. I have been using MS Windows since v3.0. Prior to that I did have (for a short while) Comodore 64. But anyway, with Windows, I am familiar with different file types (extensions) such as... .EXE, .DLL, .ZIP, etc. Now that I am considering Ubuntu I am confronted with things like TAR, DEB, RPM, SH, TAR.GZ, and whatever else that there may be, that I have not seen yet. I was looking at downloading AVG AV Free v8.5.290 for Linux and came across four different file extensions. I'm not sure, but I guess that TAR is a "zip" file. I have no idea which one to get! :-s Could you please tell me what file extension(s) I need to be looking for when getting "stuff" for Ubuntu? I have already downloaded the OS (.ISO) for Ubuntu v9.04 but have not
done any installing yet. I am thinking about "dual boot" before I finally commit soully to Linux only. Anyway, thanks. :confused:

---

### Post by LunaticHiatus on 2009-10-27
To summarize.
.deb are Debian based distros. Ubuntu is Debian based so you want these.

.rpm are Fedora/Red hat based distro's. You can //SORTA// run them on ubuntu, but they are known to cause bugs and crash.

.tar are source files (and sometimes zipped/compressed files). They run on every distro but you have to install them yourself and put everything in its proper folder, etc. etc. etc.

just stick with .deb files for now. and most of the files you want you can find in add/remove or synaptic package manager. Which is just like an online database of .debs specific for ubuntu.

---

### Post by jmszr on 2009-10-27
Ineed2know,

The simplest file type to install is a .deb file.
The GDebi Package Installer will install .deb with ease.

---

### Post by 3rdalbum on 2009-10-27
When you install Ubuntu (there's a new version coming out in 1 day, sorry if you wasted hours downloading 9.04!) there will be a program in the Applications menu called "Ubuntu Software Center". This program can help you find software, and will download and install it for you.

That's the Linux way - use the package management program to download and install software, don't trawl the web looking for it.

If you can't find the software in the Software Center or in Synaptic Package Manager (the latter has a greater array of software), you should look online to see if there is a "PPA" (Personal Package Archive) with the software. You add the PPA's address to your Software Sources program and then you can download and install the software with your package manager.

If there's no PPA, then you should try and look for a ".deb" file, also known as a Debian package. You can double-click on this package and it will install.

Note that you don't need an anti-virus on Linux, because there are no viruses that run natively on Linux. So you can ditch AVG unless you want to scan for Windows viruses.

Glossary:

.tar.gz - A compressed archive that can contain pretty much anything (like .zip).
.deb - Debian package; that's the native Ubuntu package format for software.
.rpm - Red Hat package. Not native to Ubuntu. If it's the only option, it can be converted to a Deb.
.sh - Shell script; it's a kind of program based completely around terminal commands, therefore it runs in the terminal. Sometimes these will install software, but most people prefer to use a Debian package for certain good reasons :-)
.run / .bin - A runnable program (often a shell script).

Also, filename extensions are not usually necessary on Linux. They are retained more for cross-platform interoperability than anything else.

In short: Install with your package manager wherever possible, it's the easiest method as it downloads and installs everything for you in one step. Don't bother downloading anything with .tar.gz as it is usually the program's source code and will need to be compiled first; compiling isn't too difficult but until you find your feet with Linux you shouldn't really bother with it unless absolutely necessary.

---

### Post by martrn on 2009-10-27
Get some files and put it into a tar.
Compress it.
Package it, into a package format (ie debian style), 
And release it into a repository.

.tar ===>  .tar.gz ===> .deb

All of the ubuntu software that is popular is stored in various repositories and is upgraded on a regularly basis.  It would be daft to collect stuff as if it has bug releases fixed in the period of time you got it and the time you need to install it, you will need to re-download it and it will require re-installing.

The apt package management system manages all your packages, and you shouldn't need to look for software in the way a windows user would need to look for software.  If you get pripority software that is not in the ubuntu repositories you need to run a shell script that you usually get instructions for.

Stop thinking, collecting or "getting "stuff" and simply install.

---

### Post by Possum Films on 2009-10-27
When you are downloading a piece of software for Ubuntu it is always best to use the .deb package if there is one available. The reason that many programs come in several different package formats is because there are lots of differet Linux distributions. Formats other than .deb (such as .rpm) can be made to work on Ubuntu but may not work as well because the native package format in Ubuntu is .deb. 

A .tar.gz file works in the same way as .zip  and .cab files do under Windows and .sh files are equivilant to Windows .bat files. 

Most of the time file under Ubuntu do not actually need extensions; the Ubuntu file manager can detect the type of the file without needing to reffer to the extension (ie, a JPEG image will still open in the correct program when you double-click on it even if it was saved without the .jpg or .jpeg extension). Unlike Windows execuitibles which end in .exe, Linux ececutibles generally will have no extension.

---

