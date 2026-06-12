---
title: "need help with nmap"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by clutch| on 2009-08-09
Hey, brand new linux user here.  I've been on mac OS for years, and used windows occasionally, but zero linux experience.  I literally just installed Ubuntu 9.04 about fifteen minutes ago.

Trying to install nmap, which I downloaded  from nmap.org/download (the link that said i386 nmap - the others said 64-bit only and I have 32).  Tryed searching around here for a bit and got stuck here:

clutch@clutch-laptop:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nmap
clutch@clutch-laptop:~$ 


sorry if this is a stupid question.  I'm thinking that its looking for nmap on the CD in my optical drive, which i believe is e: and its not there for some reason?  How can I point it in the direction of the one I downloaded rather than the one that it seems to think would be on my install disc?  I tried something i read in another thread about unchecking a box in the synaptic package manager, but the box in question was unchecked to begin with.

help.  I have no idea what i'm doing.  :)

---

### Post by unutbu on 2009-08-09
Click on System>Admin>Software Sources.
You will be asked to type in your password.
Enable the "main" repository, and disable the "CD-ROM" repository.
When you close the window, Ubuntu will update its database of available packages. 

Then try installing nmap again.

PS. Welcome to Ubuntu.

---

### Post by clutch| on 2009-08-09
Yeah, that's what I tried first, and the "main" was checked and cd unchecked to begin with.  Still getting same result in terminal as what I pasted above.  Am I correct in assuming that its looking for it on the CD then?

/edit further info:

the file from nmap.org/downloads downloaded to my desktop.  icon looks like a cardboard box, file named nmap-5.00-1.i386.rpm  When I double-click, it opens up archive manager and tells me that it is not a supported archive.

idunno if that helps at all.

---

### Post by unutbu on 2009-08-09
What is the output of ```


grep '^deb .*main' /etc/apt/sources.list
sudo apt-get update
apt-cache policy nmap
sudo apt-get install nmap
```

The file you downloaded is an rpm file. Ubuntu uses deb packages mainly. It is possible to use a program called "alien" to convert rpms to deb, but in general it is much more pleasant to just find the deb in the repositories and install that.

---

### Post by clutch| on 2009-08-09
aha.  See, I knew it was something stupid, haha.  In my defense I've never even seen any form of Linux in my life until the last hour.  I just had an old laptop with no OS and a bug up my *** to try it out.

I'd paste in what I got in terminal when entering the cmnds you gave me, but its a ton of text.  Short version is, it updated, and then I'm pretty sure it downloaded the correct version of nmap and installed.  Thx a bunch, I'm sure I'll be back with more stupid questions soon.

---

### Post by lswb on 2009-08-09
> **clutch| said:**
> Hey, brand new linux user here.  I've been on mac OS for years, and used windows occasionally, but zero linux experience.  I literally just installed Ubuntu 9.04 about fifteen minutes ago.

Trying to install nmap, which I downloaded  from nmap.org/download (the link that said i386 nmap - the others said 64-bit only and I have 32).  Tryed searching around here for a bit and got stuck here:

clutch@clutch-laptop:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nmap
clutch@clutch-laptop:~$ 


sorry if this is a stupid question.  I'm thinking that its looking for nmap on the CD in my optical drive, which i believe is e: and its not there for some reason?  How can I point it in the direction of the one I downloaded rather than the one that it seems to think would be on my install disc?  I tried something i read in another thread about unchecking a box in the synaptic package manager, but the box in question was unchecked to begin with.

help.  I have no idea what i'm doing.  :)

apt-get installs packages from repositories that are listed in the file /etc/apt/sources.list. There is a version of nmap in the normal ubuntu repositories, which implies that your system was not connected to the internet when you used the apt-get command.

OTOH, the package you download from nmap.org (which is probably nmap-5.00.tar.bz2) is a source package that must be compiled and manually installed on your system; it cannot be installed by apt-get or dpkg and it won't be tracked by the package management software. (Well, not unless you make a package from the sources or use checkinstall, but that's getting a little too off topic for now)  It's called a tar file because that is an ancient unix program used to make archive files (actually originally an acronym for Tape ARchive) and the .bz2 or .gz extension indicates that the file has also been compressed with the bzip2 or gzip programs.

The main reason to use a tar file direct from a site like this, instead of the package from the repositories, is that the repositories are often a little older versions than the "latest" available directly from the project web site. (In a few cases, a lot older, but usually they are not too far behind)

In the case of nmap, or instance, the ubuntu repositories list version 4.76; nmap.org has version 5.0

So, the easiest way to install, is just connect to the internet and use the "apt-get install nmap" command and install version 4.76 or whatever is in the repositories at this time.

If you do want the absolute latest version, you will have to untar the file downloaded from nmap.org and make/install it manually. It's not that hard but you may have to install certain other packages on your system first. You can find more information about that by searching this forum., google, or on the nmap website, as well as in the documentation supplied in the tar file itself, or open a new thread with appropriate title.

---

