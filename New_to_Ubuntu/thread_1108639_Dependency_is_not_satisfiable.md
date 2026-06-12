---
title: "Dependency is not satisfiable"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by LongH on 2009-03-27
I have been trying to install the compilation toolchain on an old computer without an internet connection. I downloaded several packages on another computer and put them on a pen drive, but I do not know how to install them.
For example, I downloaded the package dpkg-dev on a pen drive. However when I double click on the icon the package installer pops up and says Error: Dependency is not satisfiable: libtimedate-perl
However, I do also have the libtimedate-perl package on the same pen drive. Can someone please explain what I am doing wrong and how to correctly install these programs.

---

### Post by Locutus_of_Borg on 2009-03-27
well, you can try this:

```

sudo -i
dpkg -i /media/disk/*.deb

```

assuming your flash drive is mounted at /media/disk

but you will need all required dependencies for all the packages you are trying to install


one way of ensuring you get all the dependencies is to boot off a live disk and apt-get install the application you want, apt will get all the dependencies, then you can copy the files from /var/cache/apt/archives/ onto the flashdrive, then do what i said above

---

### Post by BDNiner on 2009-03-27
The easiest way to download packages and install them on a computer that does not have an internet connection is to open Synaptic package manager on the computer without and internet connection and select all the packages you want to install as if you were going to normally install them. Then click on File and select Generate package download script. Name your script and save it to the pen drive. Then go to the computer that has an internet connection and run the script by typing
```

sh *name of script *

```

---

### Post by Ubuntiac on 2009-03-27
I'd strongly recommend checking out the Keryx project, which is a KDE4 Kubuntu GUI app specifically for downloading apps / updates for machines without internet, from a machine that's connected.

You can check it out at [http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by LongH on 2009-03-27
Thank you so much! I am downloading Keryx right now and it seems like just what I have been looking for. I cannot express how happy I am!

---

### Post by llamabr on 2009-03-27
Well done.  If it works, be sure to edit the subject message to indicate that the issue has been [solved]

---

### Post by Ubuntiac on 2009-03-29
> **LongH said:**
> Thank you so much! I am downloading Keryx right now and it seems like just what I have been looking for. I cannot express how happy I am!

Another happy day on the UbuntuForums. Let's hear it for community and helping each other out. :popcorn:

---

