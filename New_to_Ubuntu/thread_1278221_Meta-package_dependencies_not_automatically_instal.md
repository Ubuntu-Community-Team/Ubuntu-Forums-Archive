---
title: "Meta-package dependencies not automatically installed"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by beleriand on 2009-09-29
Hello, I'm new to Ubuntu and this is my first post on the forum.

I'm wanting to create my own meta-package to ensure that the product's various dependency packages are installed.  My "control" file looks like:

Package: example-metapackage
Version: 1.0
Section:
Priority: optional
Architecture: amd64
Depends: cabber
Installed-Size:
Maintainer: 
Description: My example meta-package.

To create my deb file, I do the following:
sudo dpkg -b example-metapackage

Good.  Now the problem is when I try to install the Debian meta-package:
sudo dpkg -i example-metapackage.deb

And I get the following error:

Selecting previously deselected package example-metapackage.
(Reading database ... 128413 files and directories currently installed.)
Unpacking example-metapackage (from example-metapackage.deb) ...
dpkg: dependency problems prevent configuration of example-metapackage:
 example-metapackage depends on cabber; however:
  Package cabber is not installed.
dpkg: error processing example-metapackage (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 example-metapackage

I tried three different dependency packages: cabber, iodine, and qualculate.  In each case, the meta-package won't install because its dependency package isn't installed.  So I'm confused, since the whole purpose of a meta-package is to ensure that dependency packages are installed.  Why doesn't dpkg automatically install the dependencies?

---

### Post by mikeyphi on 2009-09-29
I'm not heavily into programming but my understanding is that dpkg is a simple package manager and does not automatically satisfy dependencies.
Whereas, for example, the command 'aptitude' will both get a package and get dependencies.

Hope that was helpful!

---

### Post by beleriand on 2009-09-29
Thanks for the reply!

I understand now; manually installing .deb packages using dpkg won't automatically install dependent packages.

This was also helpful:
[http://www.psychocats.net/ubuntu/installingsoftwareold](http://www.psychocats.net/ubuntu/installingsoftwareold)

"The only difference between manually installing a .deb file and using *apt-get* to install a .deb file is that *apt-get* will resolve dependencies for you (if one package needs another to be installed, apt-get will install that 'pre-requisite' package). If you manually install a .deb file, you will also have to manually install its dependencies."

---

### Post by beleriand on 2009-09-29
The following seems to work for my example meta-package:

// Create the meta-package:
$ sudo dpkg -b example-metapackage

// Install the meta-package and its dependencies.
$ sudo gdebi example-metapackage.deb

// Confirm that the meta-package is installed.
$ apt-cache policy example-metapackage

// Remove the meta-package.
$ sudo aptitude purge example-metapackage

---

