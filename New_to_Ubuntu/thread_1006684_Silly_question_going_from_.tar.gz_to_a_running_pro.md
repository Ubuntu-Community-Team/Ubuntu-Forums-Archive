---
title: "Silly question: going from .tar.gz to a running program"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by SpaceMaster on 2008-12-09
Okay, I want to install a program on an Ubuntu box not connected to the internet.  Thus, I have downloaded a nice little tarball to shuttle over to it on a flash drive.  The problem is, without explicit directions, I'm a little lost.  The package, btw, is gtkpod-0.99.12.tar.gz.  Could someone give me a walkthrough on the various intermediate steps on the way to a working gtkpod?

I'll start off with step one:
```
tar -xvfz gtkpod-0.99.12.tar.gz
```

---

### Post by Michael.Godawski on 2008-12-09
The usual steps are:
Extract (the command you used), and then read the Readme file if there is one:p;

if you have to compile the package (when you see a make file in the folder),run

```
./configure
make
sudo make install
```

---

### Post by amauk on 2008-12-09
what's inside the tarball?

source files?
pre-compiled binaries?
something else?


for source, probably the usual
./configure && make && sudo make install


for binaries, probably best to do something like
sudo mkdir /usr/local/gtkpod
sudo mv gtkpod-0.99.12.tar.gz /usr/local/gtkpod
tar -xvfz gtkpod-0.99.12.tar.gz

depends on what's in the tarball

---

### Post by karlr42 on 2008-12-09
There's a much, much easier way - on a machine with net access, run 
```
sudo apt-get -d install gtkpod
```
That downloads the package file, which you can find in /var/cache/apt/archives/ . Copy that to the target machine and double click to install as if from the net :D

---

### Post by aysiu on 2008-12-09
Even without internet access, I still think it's better to go with .deb files instead of .tar.gz.

If you're using Ubuntu 8.10, download these files to a USB drive:
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.12-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.12-3_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/i/id3v2/id3v2_0.1.11-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/i/id3v2/id3v2_0.1.11-3_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0-5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0-5_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/i/id3lib3.8.3/libid3-3.8.3c2a_3.8.3-7.2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/i/id3lib3.8.3/libid3-3.8.3c2a_3.8.3-7.2_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/m/mp3gain/mp3gain_1.4.6-7_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/m/mp3gain/mp3gain_1.4.6-7_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/f/faad2/faad_2.6.1-3.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/f/faad2/faad_2.6.1-3.1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/multiverse/f/faac/faac_1.26-0.1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/f/faac/faac_1.26-0.1ubuntu2_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/multiverse/l/lame/lame_3.98-0.0_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/lame/lame_3.98-0.0_i386.deb)

Then, transfer them to the desktop of the Ubuntu computer, and then type these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

