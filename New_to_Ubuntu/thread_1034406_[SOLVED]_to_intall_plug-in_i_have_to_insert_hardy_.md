---
title: "[SOLVED] to intall plug-in i have to insert hardy disk!?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by adamogardner on 2009-01-08
I've seen this before where I want to install a package and it requires that I put my installation disk in drive.  I always back out because I don't understand what's happening.  Is it safe to do that?  Whay does it need my disk?  Can I use an install disk other than the one I physically used to install my operating system?

---

### Post by Titan8990 on 2009-01-08
Just comment out the the CD line (usually the first one) in /etc/apt/sources.list

---

### Post by adamogardner on 2009-01-08
> **Titan8990 said:**
> Just comment out the the CD line (usually the first one) in /etc/apt/sources.list

So I comment out the first line here with a '#' sign?  In the spirit of knowing what what does before one does it, could it be explained what this file does, what this line does, and under what conditions do I get this request for install disk?

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

---

### Post by the yawner on 2009-01-08
Or just go to System>Administration>Software Sources and uncheck the option/s under Installable from CD-ROM/DVD.

> **adamogardner said:**
> So I comment out the first line here with a '#' sign?  In the spirit of knowing what what does before one does it, could it be explained what this file does, what this line does, and under what conditions do I get this request for install disk?

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
The file mentioned contains on a default installation all software repositories from which you may install software for Ubuntu. That includes the CD installer if it's uncommented/enabled. Basically the OS requires that it must be able to access all software repository, even the CD.

---

### Post by sisco311 on 2009-01-08
*The file is basically the roadmap for your system to know where it may download programs for installation or upgrade.*
[https://help.ubuntu.com/community/SourcesList]("https://help.ubuntu.com/community/SourcesList")
[https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")
[https://help.ubuntu.com/community/Repositories]("https://help.ubuntu.com/community/Repositories")

---

### Post by aloshbennett on 2009-01-08
In ubuntu, when you want vlc player installed, you say "apt-get install vlc". Ubuntu takes care of finding the installable files for vlc player, find out what other module is needed, gets that too and installs all of them for you.

How it does is, ubuntu has a list of repositories which contain all the popular applications. One such repository is the ubuntu installation disk.

/etc/apt/sources.list contains the list of repositories ubuntu checks for installable files.

1. Its absolutely safe to insert the cd when asked to.
2. You need not put the same disk you used for installation. Any ubuntu installation cd for the same distribution (hardy) would do.
3. If you edit out that line, you are removing cdrom from the list of repositories. Your OS would then go and check with other repositories mentioned in the file over the internet.

---

### Post by Captain_tux on 2009-01-08
> **adamogardner said:**
> So I comment out the first line here with a '#' sign?  In the spirit of knowing what what does before one does it, could it be explained what this file does, what this line does, and under what conditions do I get this request for install disk?

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

Damn good question... 5 Schrute bucks for you!

---

