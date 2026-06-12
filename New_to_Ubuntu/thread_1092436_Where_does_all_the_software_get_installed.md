---
title: "Where does all the software get installed?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by =CrAzYG33K= on 2009-03-10
Newbie to Linux.. :)

One question, in Windows, we did have an authority as to which location we needed to install software into..

Is that not there in Linux (or Ubuntu)?

Is there a default path like (/usr/lib/ or something) where the new software is installed into?

---

### Post by lingnoi on 2009-03-10
Usually binaries from .debs are installed into /usr/bin

This is important because it means you can just type the binary's name in the command line without have to specify the full address.

If you compile your own software with "make install" in ends up in /usr/local/bin

There are many exceptions to this, however I am trying to keep it simple.

---

### Post by Cresho on 2009-03-10
I run about 20% of my software in my "installed_programs" directory.  If you don't want to install it in ubuntu, you can just grab the binary version and extract it in a folder and just run it from there.  It's like an exe running off your desktop.

Yes you have freedom.

---

### Post by =CrAzYG33K= on 2009-03-10
Ok.. So from what I gather so far...

If I grab the .deb files (Ubuntu Synaptic Package Manager format) - it'll go to '/usr/bin'
If I grab a .bin file -> I can install in my directory of choice.
Right ?

And if I get hold of a .bin file, do I need to compile and install it ?

---

### Post by oldos2er on 2009-03-10
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by bodhi.zazen on 2009-03-10
packages install various things in various locations.

In Linux things are organized by function.

So binaries go in /bin , /sbin , /usr/local/bin , etc

man pages go with the other man pages

lib go with the other libraries

etc

You should look at how the file system is organized :

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

OK, got it ?

Now if you are installing something from outside the packaging system (apt or dpkg) you will need to look at how the package is to be installed, ie read the README.

In general if you are installing in this way use /usr/local

a .bin is generally an installer (which is packaged in general by someone who does not understand the Linux file system or apt).

For more specifici advice, what are you trying to install and why are you not using the repositories ?

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[http://www.debian.org/doc/FAQ/ch-pkg_basics](http://www.debian.org/doc/FAQ/ch-pkg_basics)

---

### Post by =CrAzYG33K= on 2009-03-11
^ Much Appreciated. Thanks.

---

### Post by SunnyRabbiera on 2009-03-11
> **=CrAzYG33K= said:**
> Ok.. So from what I gather so far...

If I grab the .deb files (Ubuntu Synaptic Package Manager format) - it'll go to '/usr/bin'
If I grab a .bin file -> I can install in my directory of choice.
Right ?

And if I get hold of a .bin file, do I need to compile and install it ?

I would avoid downloading a .bin from some site somewhere, its usually best to use a .deb or use a repository.
Most of what you need is in the repositories.

Anyhow as for where installed apps go there are two directories it will go:
usr/bin and usr/lib
Usually a good chunk of your apps go to usr/bin, though I know a few that go to usr/lib.

---

