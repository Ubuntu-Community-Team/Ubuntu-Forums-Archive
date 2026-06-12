---
title: "help with downloading activepython"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by ntmiller on 2010-04-01
i've tried to install active python with no luck when i type ./install.sh -h i'm told command not found i've even tried sudo aptitude install /ActivePython-2.6.5.12-linux-x86_64.tar.gz i'm then told reading package lists done building dependency tree reading state information done readin extended state information done reading state information initializing package states done couldn't dind any package whose name or description matched "/ActivePython-2.6.5.12-linux-x86-64 

any help would be of great use to me
thank you in advance

---

### Post by 3rdalbum on 2010-04-02
> **ntmiller said:**
> i've tried to install active python with no luck when i type ./install.sh -h i'm told command not found

You're in the wrong directory; your terminal is in a directory that doesn't contain the command you're trying to run. You need to navigate to the directory that contains the "install.sh" script, it's inside the folder that you've extracted.

If you don't know how to navigate the terminal to the correct directory, then you could just drag the "install.sh" script onto the terminal and add the space and the -h.

> i've even tried sudo aptitude install /ActivePython-2.6.5.12-linux-x86_64.tar.gz

Apt-get and aptitude only install packages that are in the repositories, not Zip files that are on your desktop.

---

### Post by ntmiller on 2010-04-02
thanks for the advise i am new to all this so things a going a little slow but i will try and see if i cant make heads or tail out it here is to a long night of me and ubuntu...... :KS

---

### Post by ntmiller on 2010-04-02
what is the difference between ./install.sh no such file or directory and install.sh command not found?

---

### Post by srid on 2010-04-12
Open Terminal and run the following commands:

(NOTE: go to [http://downloads.activestate.com/ActivePython/releases](http://downloads.activestate.com/ActivePython/releases) or activestate.com/activepython to find the download URL for your platform and latest version)

```

cd /tmp
wget http://downloads.activestate.com/ActivePython/releases/2.6.5.12/ActivePython-2.6.5.12-linux-x86_64.tar.gz
tar zxf ActivePython-2.6.5.12-linux-x86_64.tar.gz
cd ActivePython-2.6.5.12-linux-x86_64
sudo ./install.sh

```

After pressing ENTER for the questions, you can run Python by running ths command

```

/opt/ActivePython-2.6/bin/python

```

You may optionally add that bin directory to your $PATH.

---

### Post by rrashkin on 2010-04-12
I'm curious.  What does ActivePython buy you over the Python installed with Ubuntu?

---

### Post by srid on 2010-04-12
> **rrashkin said:**
> I'm curious.  What does ActivePython buy you over the Python installed with Ubuntu?

1. Commercial support: See [http://stackoverflow.com/questions/1352528/why-does-activepython-exist](http://stackoverflow.com/questions/1352528/why-does-activepython-exist)

2. Upcoming development tools: PyPM [pypm.activestate.com] (though apt-get will work too) and other tools like cross-platform deployment (.deb, .exe, .dmg) and so on.

---

