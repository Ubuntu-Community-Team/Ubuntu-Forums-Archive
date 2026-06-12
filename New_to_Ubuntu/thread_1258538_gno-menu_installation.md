---
title: "gno-menu installation"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Kristofer Van Orton on 2009-09-05
Okay so I downloaded gno-menu
(gnomenu-1.9.9.tar.gz)
i extract and go to the read me file
it says

INSTALL:
sudo make install

which doesnt help me at all
i realize its a command
but how do i use it?
(sorry im still quite a noobie)

thanks in advance
(assuming someone will help :P)
-KVO

---

### Post by Liolikas on 2009-09-05
Try to:
sudo apt-get install gnomenu

Without downloading anything at all separately.

---

### Post by Kristofer Van Orton on 2009-09-05
it came out with this, should i be putting the package somewhere else? right now its in my data partition


```
kris@ubuntu:~$ sudo apt-get install gnomenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnomenu
```

---

### Post by Liolikas on 2009-09-05
What you want is .deb (Debian package) file.
.tar.gz (source code file) is possible to use, but avoid them as much as possible.
I found here deb for you:
[https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6)

Better add Ubuntu bug (feature request) for gnomenu in Synaptic (apt-get).

---

### Post by wojox on 2009-09-05
First make sure you have build essentials:

```
sudo apt-get install build-essential
```

Then go into the directory where the files are and run:

```
sudo make install
```

---

### Post by Kristofer Van Orton on 2009-09-05
well it worked just setting it up with gdebi package installer but now how to i get to it so i can theme it

nvm i figured it out thanks all for the help

---

### Post by 3rdalbum on 2009-09-05
> **Liolikas said:**
> Try to:
sudo apt-get install gnomenu

Without downloading anything at all separately.

Why didn't you check if Gnomenu was in the repositories before telling him to try that??!

Kristofer: Generally, you should try to stick to software from the software repositories, as it's easier to install.

The package you have downloaded is actually source code that you have to compile, and it can be tricky for new users to do this until they know how it works.

You must open a terminal (Applications > Accessories > Terminal) and navigate the terminal* to the folder that contains the source code (the folder you extracted from the archive). Then type whatever commands the INSTALL file tells you to run; usually:

```
./configure
make
sudo make install
```

**In order to compile anything, you must have the build essentials.** You can get the "build-essential" package from Synaptic Package Manager. 

When you are compiling software, the process might stop and give you an error message that you are missing a particular library. At this point, note down the name of the library and try and find it in Synaptic. Install the *development headers* version of the package, which has a name ending in "-dev". For instance, if it says that you're missing GTK 2.x, then go to Synaptic and install the "libgtk2.0-dev" package.

Then start running the compiling process again.


*If you don't know how to navigate in the terminal, then install the "nautilus-open-terminal" package, and when you next log in you'll have an option in your right-click menu to "Open In Terminal".

---

### Post by Liolikas on 2009-09-05
>Why didn't you check if Gnomenu was in the repositories before telling him to try that??!
Because I do not use Ubuntu. I am Gentoo user.

---

### Post by Kristofer Van Orton on 2009-09-05
I already got build essentials before I even posted this, but thanks for the advice, I'm definetley going to save it for future reference.

---

