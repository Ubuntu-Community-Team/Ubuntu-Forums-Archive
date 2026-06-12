---
title: "[SOLVED] Feisty and Console Emulators"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by linux.convert on 2008-12-10
Im trying to install an emulator, zsnes151src.tar.bz2 OR ZSNES.
Ive been going off this site for handling tar balls...

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

When I get to step 3, running the **make** command my terminal says this..

**make: *** No targets specified and no makefile found.  Stop.**

even though there are makefiles in the folder...

Ive tried skipping to step 4 and running **su**...
[B]
su: Authentication failure
Sorry.
[/B]
and conversly running **sudo make install**

[B]Password:
make: *** No rule to make target `install'.  Stop.
[/B]

...and thats it, I got nothing, I dont know what to do, any help at all would be great.

---

### Post by adult swim on 2008-12-10
when you run ./configure, does it return errors at the end?

---

### Post by linux.convert on 2008-12-10
yes this...

[B]configure: error: C compiler cannot create executables
See `config.log' for more details.[/B]

---

### Post by adult swim on 2008-12-10
have you installed the package build-essential?

---

### Post by cdmike2k8 on 2008-12-10
You might be missing some packages.  Try opening a terminal, and running ```
sudo apt-get install build-essential
``` post the output of this command.  Also should read the README to see if there are other required packages.

---

### Post by cdmike2k8 on 2008-12-10
You will also need to install SDL, libsdl1.2-dev First, if you have it extracted in your home folder (/home/username), rename the folder and the downloaded file.  Then open a terminal and run these commands: ```

sudo apt-get install libsdl1.2-dev build-essential
cd ~
wget http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2
tar -xvf zsnes151src.tar.bz2
cd zsnes_1_51/src
./configure
make
sudo make install

```
Post if you get an error any way along the process.
What you are doing here is changing to your home directory, installing libsdl1.2-dev and build-essential downloading the archive, extracting it, running the configuration utility, making the installer, and then installing it.

---

### Post by linux.convert on 2008-12-11
I ran everything up to ./configure

and when I ran it I got this...

[B]ME@ME-laptop:~/GAMES/EMULATORSnROMS/zsnes_1_51/src$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
[/B]

---

### Post by cek on 2008-12-11
Any particular reason you are installing from source rather than through apt?

The version of zsnes in hardy appears to be the same as you are trying to install (1.510-2)

sudo apt-get install zsnes

---

### Post by zvacet on 2008-12-11
@ **linux.convert**

Title of your thread suggested that you are runuing Feisty,and that can be source of your problem.Feisty is not suported anymore.Install Hardy if you want LTS or Intrepid as last version.If you don't have separate home partition make one following [this]("http://www.psychocats.net/ubuntu/") guide.If you allready have it just install newer version of Ubuntu on top of it and **don't format** home partition.

---

### Post by jmcgovern on 2008-12-11
I believe OP says in the topic he's using Feisty, not Hardy.  Feisty repos are no more as of October.

EDIT: zvacet beat me to it.

---

