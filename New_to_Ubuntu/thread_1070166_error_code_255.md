---
title: "error code 255"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by BriMan on 2009-02-14
I am trying to load an HP driver for a C7280.

I have encountered the following:

Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255

Maybe because of this:

|error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)

What do I do next? I dont know how to disable the source above...

---

### Post by Partyboi2 on 2009-02-16
Open a terminal (Applications>Accessories>Terminal) and open your sources.list file
```
gksu gedit /etc/apt/sources.list
```
then make sure you have a # in front of the deb cdrom line eg.
```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090204)]/ jaunty 
```
then save if you made any changes and back in the terminal
```
sudo aptitude update
```

---

