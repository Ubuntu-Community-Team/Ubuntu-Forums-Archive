---
title: "help in installing"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by puleo1333774 on 2008-12-20
how can i install my downloaded file?

this is the file name, FretOnFire-1.3.110.tar.gz.gz:(

---

### Post by Titan8990 on 2008-12-20
In Ubuntu, you want to install via the Synaptic Package Manager. You can install from a tar.gz like the one you have found but it is more difficult and only needed if the program can't be found in the Synaptic Package Manger.

Do the following:

go to:

System -> Administration -> Synaptic Package Manager


Search for Frets on Fire.

Right click on it and select install.

Now click apply.


The Synaptic Package Manager will download and install the game for you.

---

### Post by puleo1333774 on 2008-12-20
can i use the terminal?

---

### Post by Titan8990 on 2008-12-20
Yes, I prefer that method personally but the terminal occasionally scares off new users.

To search for the package name:


apt-cache search frets on fire


To install:

sudo apt-get install fretsonfire


The above may not be the actual package name and you may have to replace fretsonfire with the package name that showed up in your apt-cache search.

If you want to learn to install a tar.gz from the CLI, i can help you do so but a graphical game is not something to start with as they typically need lots of things installed prior to installing them that apt-get and the Synaptic Package Manager takes care of for you.

---

### Post by puleo1333774 on 2008-12-20
it says "couldnt find package fretsonfire

---

### Post by wwusnobrdr on 2008-12-20
It is kind of odd to have two .gz at the end, but typically you do "tar xzvf filename.gz"  Once this is done it depends if there is a configure script or whatnot in the package.  but you either do ./configure then sudo make then sudo make install, or whatever else is recommended in the documentation.  

If you want to install it from apt-get you will need to enable the universe repositories first.

---

