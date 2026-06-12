---
title: "Xubuntu remote desktop"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by henryleestl on 2007-11-13
Ok, first of all,  i have to admit that i'm a newbie to this linux thing.
so here's my situation: i have an old desktop sitting in the corning of my room which i want to set up as a ftp server, but i don't want to attach a monitor/mouse/keyboard to it. so i want to set up some kind of remote desktop so i can control it from my laptop. i formatted a hard drive and installed the latest xubuntu 7.10, and i tried to install freenx on it. freenx requires openssh-server to run, but the command 
sudo apt-get install openssh-server
returns an error msg saying the package cannot be found. i searched through numerous forums, all of them saying that command should install the openssh-server for me. any bright ideas? thanks.

---

### Post by daflame on 2007-11-18
The answer is probably the packages selected in your /etc/apt/sources.list.  I'm not entirely familiar the package management system in Xubuntu, but in Kubuntu you can open adept and choose manage repositories and enable all repositories.

Make sure you close all package management programs before you begin.  On the command list you can type:
```

sudo nano /etc/apt/sources.list

```

when the edit screen pops up uncomment the other sections that start with deb or deb-src.  Crtl-X and enter to save it.  Then type:
```

sudo apt-get update

```

If you are interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If you need other dist packages, please let me know and I'll start a VM to build one.

---

