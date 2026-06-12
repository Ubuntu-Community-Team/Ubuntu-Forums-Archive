---
title: "Trying to install picard 1.12"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Daremo_06 on 2009-11-21
I am trying to install Picard Musicbrainz from here

[HTML]http://musicbrainz.org/doc/Picard_Download[/HTML]

in the gz I am following the install.txt.

Tells me to run 

```
python setup.py config
sudo python setup.py install
```

When I do, I get this

[PHP]rob@rob-desktop:~/Desktop/picard-0.12.1$ python setup.py config
running config
checking for pkg-cfg... yes
checking for libofa... (pkg-config) no
checking for libavcodec/libavformat... (pkg-config) no
checking for directshow... no
saving build.cfg
rob@rob-desktop:~/Desktop/picard-0.12.1$ sudo python setup.py install
[sudo] password for rob: 
running install
running build
generating scripts/picard from scripts/picard.in
running build_py
running build_ext
building 'picard.util.astrcmp' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c picard/util/astrcmp.cpp -o build/temp.linux-i686-2.6/picard/util/astrcmp.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
error: command 'gcc' failed with exit status 1
rob@rob-desktop:~/Desktop/picard-0.12.1$ [/PHP]

The install text states the following libraries

```
* Python 2.5 or newer
   http://python.org
 
 * PyQt 4.1 with Qt 4.2 or newer
   http://www.riverbankcomputing.co.uk/software/pyqt/intro
   http://www.trolltech.com/products/qt/

 * Mutagen 1.11 or newer
   http://code.google.com/p/quodlibet/wiki/Development/Mutagen

 * libdiscid (optional)
   http://musicbrainz.org/doc/libdiscid

 * FFmpeg (optional)
   http://ffmpeg.mplayerhq.hu/

 * libofa (optional)
   http://code.google.com/p/musicip-libofa/
```

Maybe I am using synaptic wrong, but its a real pita to figure out if you have something installed sometimes because the descriptions are not clear.  So my questions are...

1.  What is the easiest way to determine if I have those libraries installed?  ie command line to run?

2.  If I do have them installed, then what is causing the install to fail?

Thanks

---

### Post by steveneddy on 2009-11-21
Dude - I went to the download page and saw the Ubuntu downloader.

Delete whatever you downloaded and open a terminal, copy and paste this in terminal:

```
sudo apt-get install picard
```

Easy as pie.

---

### Post by Daremo_06 on 2009-11-21
The deb is 1.11 which has a few bugs in it.

I am already running it and I want to move up to the newest release.

---

### Post by twisted_steel on 2009-11-21
Do you have the build-essential package installed?  It looks like it can't find the C++ compiler.

---

### Post by steveneddy on 2009-11-21
> **Daremo_06 said:**
> The deb is 1.11 which has a few bugs in it.

I am already running it and I want to move up to the newest release.

Look at the Ubuntu Resources link in my sig.

Might be a good idea to read all of the links in my sig.

---

### Post by hachre on 2009-12-26
If this problem still exists:
This is for 9.10 Karmic only.

Add the MusicBrainz PPA by doing:
> sudo add-apt-repository ppa:phw/ppa
sudo apt-get update

Then install it by:
> apt-get install picard picard-plugins

More info on the PPA:
[https://launchpad.net/~phw/+archive/ppa](https://launchpad.net/~phw/+archive/ppa)

---

### Post by Podex on 2010-01-13
> **hachre said:**
> If this problem still exists:
This is for 9.10 Karmic only.

Add the MusicBrainz PPA by doing:


Then install it by:


More info on the PPA:
[https://launchpad.net/~phw/+archive/ppa](https://launchpad.net/~phw/+archive/ppa)

Thanks a lot for this hachre!

---

### Post by Podex on 2010-01-30
Btw, the bug report for updating Picard to the current version on Lucid is here: [https://bugs.launchpad.net/ubuntu/+source/picard/+bug/508225](https://bugs.launchpad.net/ubuntu/+source/picard/+bug/508225)

---

### Post by Endolith on 2010-03-04
> **hachre said:**
> If this problem still exists:
This is for 9.10 Karmic only.

Add the MusicBrainz PPA by doing:



Thanks!  This is very helpful, unlike steveneddy

---

### Post by Daremo_06 on 2010-03-05
> **Endolith said:**
> Thanks!  This is very helpful, unlike steveneddy

I completely agree!  He does have some really good info in his links, but the attitude turned me off.

---

