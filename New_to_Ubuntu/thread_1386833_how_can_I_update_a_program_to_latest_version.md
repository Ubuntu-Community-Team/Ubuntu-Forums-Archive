---
title: "how can I update a program to latest version"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by ave2 on 2010-01-21
I am currently running ultimate edition which comes with Ktorrent 3.1.2 
I see that on their website version 3.3.3 is out.

[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads)

How do I update the version that is running on my machine to the latest one. 
Any help would be greatly appreciated.

---

### Post by MaindotC on 2010-01-21
I'm not going to tell you step by step, but I'll give you some direction.  Whenever you download an application from Synaptic or via apt-get, you are getting it from a [Repository](https://help.ubuntu.com/community/Repositories/Ubuntu) in the form of a [DEB file](http://en.wikipedia.org/wiki/Deb_%28file_format%29).  If the latest version is not in the repository, you can find [other repositories](http://is.gd/6JdhB) that may or may not have the latest version available.  Most of the repositories for any software package are hosted by [Launchpad](https://launchpad.net/).

If you look in your /etc/apt/sources.list file you'll see a bunch of url's.  When you find a repository that has whatever version you want installed, you can just add the url to your sources.list, assuming you can trust the repository not to install malicious code onto your system, and then run:
```

sudo apt-get update && sudo apt-get upgrade

```

You can also download the deb file directly from the repository and double-click the file to install it.

You can also install the package from source via [Ktorrent's instructions](http://ktorrent.org/?q=downloads) coupled with a [Psychocats tutorial on how to install software in Ubuntu](http://www.psychocats.net/ubuntu/installingsoftware).

---

### Post by celticbhoy on 2010-01-21
> **ave2 said:**
> I am currently running ultimate edition which comes with Ktorrent 3.1.2 
I see that on their website version 3.3.3 is out.

[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads)

How do I update the version that is running on my machine to the latest one. 
Any help would be greatly appreciated.

Download the .tar.bz2 file to your home directory, then open a terminal and simply copy and paste the instructions from the web site :-

tar -xvjf ktorrent-3.X.Y.tar.bz2
cd ktorrent-3.X.Y
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install

It is best to do them one line at a time and that way you can see where any errors occur - if there are any.

---

