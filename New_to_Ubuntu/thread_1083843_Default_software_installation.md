---
title: "Default software installation"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by dreamcatcher_omerta on 2009-03-01
Hello guys , I installed Ubuntu 8.10 on my system yesterday .I have been installing  software using apt-get and dpkg .My question here is what's the default location for ubuntu to install softwares? and can this be changed when I am using apt-get.


Aditya

---

### Post by oldos2er on 2009-03-01
Files in a package do not go to one single location, instead they are spread out through /usr/bin, /etc, /lib, etc. You can see where each file has been installed in Synaptic Package Manager, or run
```
dpkg -L [packagename]
```
in a terminal, and replace [packagename] with the package you're interested in.

---

### Post by dreamcatcher_omerta on 2009-03-01
Thanks i got it now.Can you please explain the logic behind files not being installed in a single directory and how can i control the installation path of the software that i install.


Aditya

---

### Post by oldos2er on 2009-03-01
I don't know of a way to force installation in a particular directory.

 Here's some info on Linux file system structure: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

 What exactly are you trying to accomplish?

---

### Post by dreamcatcher_omerta on 2009-03-01
My idea is to have all the executables in a directory or know the directories in which the executables are, so that i can add them to the path variable.In simpler words i want to know the directories where executables are stored.






Aditya

---

### Post by oldos2er on 2009-03-01
Executables of most user-installed packages are in /usr/bin . This should already be in your path.

---

### Post by snova on 2009-03-01
> **dreamcatcher_omerta said:**
> and can this be changed when I am using apt-get.

No.

> **dreamcatcher_omerta said:**
> Thanks i got it now.Can you please explain the logic behind files not being installed in a single directory and how can i control the installation path of the software that i install.

This goes back to the ancient days of Unix. Personally, I don't think the original reasons stand up very well anymore- but it's deeply ingrained in pretty much all software by now.

I saw a link on the subject a while ago, but the website seems a bit messed up at the moment. (It was on GoboLinux's home page somewhere- a distro with an unusual filesystem layout.)

> **dreamcatcher_omerta said:**
> My idea is to have all the executables in a directory ...

They're already like that. :)

> ... or know the directories in which the executables are, so that i can add them to the path variable.In simpler words i want to know the directories where executables are stored.

Like oldos2er said, they're already in PATH.

/usr/bin contains most programs you'll ever run.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

