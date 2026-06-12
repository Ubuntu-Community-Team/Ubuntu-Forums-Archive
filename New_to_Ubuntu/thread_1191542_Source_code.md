---
title: "Source code"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-19
hai everyone!
where I can get source code of any Ubuntu programm?
and the second question is: if any error I will find can I send directly to Lounchpad? 
thanks

sorry for bad english. correct me please. )

---

### Post by Michael.Godawski on 2009-06-19
I would start looking here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Once you find your package, on the right side there is a link to download the source code.

---

### Post by Rubicon_82 on 2009-06-19
Hi,

Alternatively, you can do the following:

A:  Enable the source repositories.  To do this, add 'deb-src' lines to your /etc/apt/sources.list for each repository you're interested in.  E.g. if you have the following line in sources.list:
```

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```
You'd need to add the following line to get code from that repository.
```

deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

Third-party (non Ubuntu) repositories may not provide source code.

B: Update your package descriptions:
```

sudo apt-get update
```

(Note that (A) and (B) can probably be done from within Synaptic etc.)

C:  Get the source code for the package you're interested in.  You should **not** run the following command as root (sudo).  The code will be downloaded to the current directory
E.g.
```

mkdir -p ~/src/amarok
cd ~/src/amarok
apt-get source amarok

```

If you plan on compiling something obtained from the repositories, you should run 'apt-get build-dep' to obtain the dependencies for the package.  Before compiling anything, you'll also need the 'build-essential' package, which brings in the GNU compiling tools such as gcc and make.
```

sudo apt-get install build-essential
sudo apt-get build-dep amarok

```

---

