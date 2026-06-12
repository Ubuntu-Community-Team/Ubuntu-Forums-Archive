---
title: "confusion installing different types of softwares"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by zaafar on 2011-03-29
hi everyone, i am a beginner using ubuntu 10.10 and i am confused there are so many different types of files for installing software. e.g    .tar.gz , .rpm ., .deb .etc and different methods e.g synaptic package manager , software centre to install them.

can anyone please tell me what is the difference and is there any documentation available explaining all this  for a novice like me :(..

---

### Post by Paqman on 2011-03-29
Synaptic and Software Centre (and Update Manager and apt-get on the command line) are all different ways of interacting with the same thing: your package manager.

The package manager is an integral part of the system and handles installing, removing and upgrading software. It's what makes your system stable and secure. To install or remove software on Ubuntu, always use the package manager. Ubuntu Software Centre is the first place you should go. We generally don't go to websites and download software from them directly like on Windows or OSX.

Installing a .deb package manually from a website (ie: download and double-click) will also use the package manager, and sometimes this is the only option, but that's quite rare.

Rpm is for Red Hat based Linux systems (Ubuntu is Debian-based), so you can't normally use it. Tar.gz is just an archive file, it could contain anything, and if you're new you should avoid them like the plague. I'm not new, and I avoid them like the plague too. There's almost always a better option.

---

### Post by Tmcarr on 2011-03-29
Well, this is alot simpler than you might think.

In general the following filetypes have specific uses:

.tar.gz = Source code that can be compiled
.rpm = Red Hat packages (Also used in other distributions like SUSE)
.deb = Debian Packages (Used in Ubuntu since it was based on Debian)

Basically, as a general user you should only need to worry about .deb files. Synaptic makes it easy to manage these just type alt + F2 and type in gksudo synaptic. It will ask for your password, and then bring up a window that will let you search for programs and install them!

Good luck, and have fun!

---

### Post by zaafar on 2011-03-29
thanx guyz , actually i ve been using windows and these ubuntu terms are new to me .i ve switched to ubuntu to find out what it is and  i want to learn ,
 do u guyz recommend any documentation for me to learn everything about ubuntu or should i be more patient and keep using it as general user ?

---

### Post by Locke_99GS on 2011-03-29
Using it as a general user will allow you to acclimate to the system - you will learn as you go in a pace you set.

Ubuntu is just Linux with a particular software stack, package management system, and code of conduct.  

The package management and most software packages (including fixes and tweaks to individual packages) come originally from the Debian distribution. Debian creates its packages from development sources. This is described as a stream, with the software developers being at the top of the stream, then Debian, then Ubuntu (then even distributions based on Ubuntu, such as Mint) Anything above Ubuntu in this stream (or above whoever you're talking to) is considered "upstream", and most generally refers to the top of the stream. Debian is upstream of Ubuntu, and Mint is downstream of Ubuntu.

Debian uses dpkg and apt as its core package management solution. The package manager will use these tools to sort out package dependencies and download and install missing and required dependent packages, then the requested target package. This system is also used for removing packages, maintaining your software stack, and upgrading the system.

Prior to the Debian method of package management, "dependency hell" was a common occurrence among *nix users, as one package might depend on another, and that may depend on another, and sometimes different versions of those dependencies break their ABI and thus become incompatible, so certain versions of them are required. It was a horrible experience having to deal with these problems, but they mostly do not exist any more and all other popular competing package management systems have used similar methods of dependency resolution to prevent this problem. Compiling from source may lend you into this dependency hell, as there is no involvement from apt, and these would have to be sorted out manually.

Since Ubuntu is based on Debian, most Debian practices will work in Ubuntu, but since Debian (and thus Ubuntu and it's derivatives) are based on the Linux kernel (and core GNU softwares) then nearly any software written for Linux generically can be compiled from source and installed on your system.

There is a lot of information on the specifics of Ubuntu and Debian on the net, and even more on Linux in general. I would suggest *Google*, as there is no single end-all-be-all Linux bible - there is just far too much information.

edit: that was a bit longer than I originally intended.

---

### Post by arochester on 2011-03-29
Look at this: "Installing Software in Ubuntu" - [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by zaafar on 2011-03-29
thanx a lot

---

