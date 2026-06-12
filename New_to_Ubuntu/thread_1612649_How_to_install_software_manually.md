---
title: "How to install software manually"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Snake4eva on 2010-11-03
I tried using synaptic package manager, and it said I didn't have enough dependencies, note I don't have the net at home that is why I want help with this. I tried sudo apt -get install <software> but ubuntu said that I need to install java-6-jdk package. So I would like help on how to manually install packages that come with ubuntu, offline packages using the terminal and offline packages using synaptic or aptitude.

---

### Post by janpol on 2010-11-03
If you have the .deb package, you can just double clic on it, or run from a terminal:

```
sudo dpkg -i filename.deb
```

But, if it says you are missing a package it depends on, you'll have to install that package first, you can't bypass that. If you are a Windows user, is the same case when Windows claims that it needs some version of the .NET framework in order to install something.

Now, if you have a source package (normally .tar.gz or .tar.bz2) first you have to untar it (note: you'll have to install required dependencies too):

```
tar -xvzf package.tar.gz
```

or

```
tar -xvjf package.tar.bz2
```

And then cd into the directory and run this commands (I recommend to READ the INSTALL/README file first):

```
./configure
make
sudo make install
```

---

### Post by Frogs Hair on 2010-11-03
Sorry misunderstood OP

---

### Post by sikander3786 on 2010-11-03
The best one I ever found for offline installations is the Keryx Project.

[http://keryxproject.org](http://keryxproject.org)

The second best for me is APTonCD

[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

This page also lists some options.

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

### Post by Crazedpsyc on 2010-11-03
It is best to let the dependencies install as they are usually completely necessary parts of the program. that program needs to run something in java and can't be run without it

---

### Post by ubudog on 2010-11-03
AptOnCd is great software.  Very useful.

---

### Post by Frogs Hair on 2010-11-03
I thought this was what the OP was looking for and my be of interest for future use . 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

