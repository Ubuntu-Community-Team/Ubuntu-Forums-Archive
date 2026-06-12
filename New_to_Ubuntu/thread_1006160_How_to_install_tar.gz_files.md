---
title: "How to install tar.gz files?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by kinngg on 2008-12-09
I have a tar.gz file game for neverwinter nights, how do i Install that into my ubuntu 8.10?

---

### Post by dannytatom on 2008-12-09
Extract it
Open up the terminal and cd to the folder
run "make"
run "sudo make install"

Some things require more than that, but if it does, it'll (hopefully) have a Readme file in the archive. ;o

---

### Post by jamesrl on 2008-12-09
I assume the tar.gz file contains the source code and you have to build it yourself.

The standard procedure is:
```

tar xvfz neverwinter.tar.gz 
cd neverwinter (or whatever dir it extracts the files to)
./configure
make
sudo make install

```
Sometimes when installing things that were written in python (instead of standard C/Fortran/C++), you do
```
python setup.py build
sudo python setup.py install
```

EDIT: You can tell the difference between which type you need, by listing the files in the directory.  If there's a "Makefile" you need the top method, if there's a "setup.py" you need the bottom method.

---

### Post by jamesrl on 2008-12-09
If this doesn't work (and sometimes it doesn't), you can check the readme or post the error messages.  Usually an install won't work if you say need some source code dependencies (it'll give you a message like can't find qt4), and that tells you that you need to install something like qt4-dev or lib-qt4-dev, which you can usually find in synaptic pretty quickly.

---

### Post by DaveyG on 2008-12-09
Also, make sure you have build-essentials installed, if you're going to try the standard procedure as Jamesrl posted :)

---

### Post by igknighted on 2008-12-09
Well... the above mentioned are "typical" I guess, but hardly cover every situation.

A tar.gz (or tar.bz2) is a compressed archive (this is what a zip file is in windows).  Inside can be anything.  You could find C/C++ source (./compile && make && sudo make install, as mentioned above), the python code mentioned above, or any number of other things (a .deb package, a .rpm package, an autoconf script, precompiled binaries with all libraries... ie run the program from where it is, no install necessary, etc.).  In short, there is no catch-all method for installing a .tar.gz.

This all said, there is almost always a readme file included, which should have instructions on how to deal with that particular file.  It is either in the archive, or perhaps on the website you got the file from.  Always look for directions there first.

---

### Post by jamesrl on 2008-12-09
While I agree that a tar.gz is just a compressed archive, I don't think it in practice would ever be a .deb or .rpm, as both of those are already compressed archives: 
[http://en.wikipedia.org/wiki/Deb_(file_format](http://en.wikipedia.org/wiki/Deb_(file_format))
[http://en.wikipedia.org/wiki/RPM_Package_Manager](http://en.wikipedia.org/wiki/RPM_Package_Manager)

[COLOR="Gray"]
I also doubt it would be a precompiled binary unless it specified architecture type (e.g., 386/686, amd64/x86_64) in the file name (or at least when you downloaded it.)[/COLOR]  Actually looking at: [http://nwn.bioware.com/downloads/linuxclient.html#notes](http://nwn.bioware.com/downloads/linuxclient.html#notes)  it is a precompiled binary.  So follow the instructions there, and remember that when they say to extract a file, just type tar xvfz the_file_name.tar.gz in the terminal.

I also doubt it would be something like autoconf/Cmake scripts, as autoconf scripts are scripts for the developer to use, to facilitate the making of configure scripts for many kinds of *nix systems, so you can do that standard ./configure && make && sudo make install.  A user should never have to play with them.  [See for example diagram here:
[http://en.wikipedia.org/wiki/Autoconf](http://en.wikipedia.org/wiki/Autoconf)
]

It could be something else as well, like some sort of script (a bash / python) or say byte-code compiled java (that is compiled to run on java virtual machine; e.g. [ImageJ]("http://rsbweb.nih.gov/ij/download.html") comes as byte-code java in a tar.gz).[COLOR="Silver"][/COLOR]

---

