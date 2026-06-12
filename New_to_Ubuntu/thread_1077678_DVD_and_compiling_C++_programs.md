---
title: "DVD and compiling C++ programs"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by wolfman1221 on 2009-02-22
Hi, I just downloaded ubuntu and I would like to be able to watch DVDs and compile C++ programs. So how do I do that?

---

### Post by Rolcol on 2009-02-22
The fastest way would be to install the codecs and the compilers through the command line.  Open up a terminal window (Applications > Accessories > Terminal) and type in this:```
sudo apt-get install ubuntu-restricted-extras build-essential
```
It will prompt you for your password and then list all of the applications it will install.  The list should be a bit big.

If you're afraid of the terminal, you can go the GUI route to install these.  You'll end up the same way.
1) System > Administration > Synaptic Package Manager
2) Search for ubuntu-restricted-extras and check the box to install.
3) Same as #2 but search for build-essential
4) Click Apply and continue to the installation.

It will install the compilers but the compilers are command-line.  You may want to install an IDE like Code::Blocks.

---

### Post by carml on 2009-02-22
To watch dvd you can follow two ways:
1. install any of the gstreamer packages;
2. all the ubuntu restricted extras package.
To write programs in C++,install the package build-essential.
Do you know how to install programs under Linux?

There always someone quicker to type ;-)

---

