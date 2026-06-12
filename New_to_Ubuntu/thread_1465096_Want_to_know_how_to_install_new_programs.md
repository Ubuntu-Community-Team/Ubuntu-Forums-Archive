---
title: "Want to know how to install new programs?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by kapi on 2010-04-29
I've installed programs using the program manager from the repositories and synaptic and also used .deb files but am unsure what or how to install programs that I download.

I'm especially interested in Bluefish version 2.0 and have looked at their site but am a bit nervous about the process.

Can anyone please advise. . . thanks

---

### Post by werecatomega on 2010-04-29
you can already get bluefish in the software center

---

### Post by Paqman on 2010-04-29
You'll need to add their repo to get the latest version. They've got [instructions on their site]("http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer") that you can just cut and paste in.

---

### Post by leonhook on 2010-04-29
Here are the instructions from the bluefish site

Installing 2.0.0 (current stable) on Ubuntu 9.04 or newer
add the following line to /etc/apt/sources.list
deb     [http://debian.wgdd.de/ubuntu](http://debian.wgdd.de/ubuntu) jaunty main restricted universe multiverse
or put a snippet into /etc/apt/sources.list.d/

sudo wget [http://debian.wgdd.de/stuff/debian.wgdd.de_ubuntu.list](http://debian.wgdd.de/stuff/debian.wgdd.de_ubuntu.list) -N -P /etc/apt/sources.list.d

Run updates, to pick up the newly available options
apt-get update

You may see errors at this point, because you've not yet installed the cryptographic key, but that's OK as you're about to do that

Then install the repository cryptographic key and Bluefish:

apt-get install wgdd-archive-keyring
apt-get install bluefish

---

### Post by tubunu on 2010-04-29
> **kapi said:**
> and also used .deb files but am unsure what or how to install programs that I download.

To install .deb files with a double click (literally!) you must have Gdebi installed on your system. Go to Synaptic and search for gdebi or paste this in the Terminal:

```
sudo apt-get install gdebi
```

---

### Post by 3rdalbum on 2010-04-29
Find a repository or a PPA that contains the later version of Bluefish, and add it to your package manager. The site you find it on should have instructions for how to add it.

---

### Post by Paqman on 2010-04-29
> **tubunu said:**
> To install .deb files with a double click (literally!) you must have Gdebi installed on your system. Go to Synaptic and search for gdebi or paste this in the Terminal:

```
sudo apt-get install gdebi
```

Er, gdebi is installed by default on desktops, dude.

---

### Post by kapi on 2010-04-29
Thanks everyone, 

got it installed, it amazes me why we still do it this way, No don't have a go at me because I'm discussing alternatives to Ubuntu, I just think using .deb files would attract a lot more users from windows.

thanks again for all your help

---

### Post by 3rdalbum on 2010-04-29
> **kapi said:**
> Thanks everyone, 

got it installed, it amazes me why we still do it this way, No don't have a go at me because I'm discussing alternatives to Ubuntu, I just think using .deb files would attract a lot more users from windows.

Debian packages (.deb) are good, but repositories are better. Repositories contain Debian packages, and they allow the repository's maintainer to push out updates. There's also a security feature that ensures that the packages have not been interfered with in transit, that you can't really get in Debian packages on their own.

Debian packages aren't portable across distributions unfortunately, and for the most part they don't work across CPU architectures (Linux runs on x86, ARM, MIPS, SPARC, PowerPC and lots of other CPU architectures). So that's why there's always some sort of source code available that can be compiled.

Debian packages and repositories are becoming more common since Ubuntu became so popular, and since Ubuntu made it so easy to start a repository. Some day in the future, everything will be available in a repository somewhere!

Yes, Windows users might prefer Debs over repositories, but in the end Linux users like repositories, and it IS *our* operating system.

EDIT: I'm glad you got it sorted anyway. This wasn't a flame or a rant, just an explanation. :-)

---

### Post by Paqman on 2010-04-30
> **3rdalbum said:**
> 
Yes, Windows users might prefer Debs over repositories


Not once they've been using repos for a while they won't ;)

---

