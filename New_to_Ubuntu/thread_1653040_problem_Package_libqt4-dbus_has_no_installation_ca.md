---
title: "problem: Package libqt4-dbus has no installation candidate"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by ubun_tut on 2010-12-26
hi, i am trying to install this streaming video software called onto my ubuntu 8.04. there are instructions at [http://www.pps.tv/about/6/364.html](http://www.pps.tv/about/6/364.html) 

when i typed the command 
sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
and entered the password, i get the following error:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libqt4-dbus is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt4-dbus has no installation candidate

```

does anyone know how i can get around this? thanks for any help!

---

### Post by davidmohammed on 2010-12-26
not using hardy myself - but the library in questioned is mentioned [here]("http://packages.ubuntu.com/hardy-backports/libqt4-dbus") - have you enabled the backports repository through administration - software sources?

---

### Post by ubun_tut on 2010-12-26
hi, after i enabled backports repository, that problem went away, and i managed to install most of the packages. there were 2 that could not install, and the error was 

```

Failed to fetch http://mirror.nttu.edu.tw/ubuntu/pool/universe/q/qt4-x11/libqt4-test_4.4.0-1ubuntu5~hardy1_i386.deb  503 Service Unavailable 10003
Failed to fetch http://mirror.nttu.edu.tw/ubuntu/pool/universe/q/qt4-x11/libqtgui4_4.4.0-1ubuntu5~hardy1_i386.deb  503 Service Unavailable 10003
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

so i ran the update manager, and that seemed to solve the problem. the next step in the pps installation is 

sudo dpkg -i ppstream_1.0.0-1_i386.deb

but this met with many errors, as follows:

```

Selecting previously deselected package ppstream.
(Reading database ... 180160 files and directories currently installed.)
Unpacking ppstream (from ppstream_1.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of ppstream:
 ppstream depends on libqt4-core (>= 4.4.0); however:
  Package libqt4-core is not installed.
 ppstream depends on libqt4-gui (>= 4.4.0); however:
  Package libqt4-gui is not installed.
 ppstream depends on libqt4-network (>= 4.4.0); however:
  Package libqt4-network is not installed.
 ppstream depends on libqt4-webkit (>= 4.4.0); however:
  Package libqt4-webkit is not installed.
 ppstream depends on libqt4-xml (>= 4.4.0); however:
  Package libqt4-xml is not installed.
 ppstream depends on mplayer | mplayer-nogui; however:
  Package mplayer is not installed.
  Package mplayer-nogui is not installed.
dpkg: error processing ppstream (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ppstream

```

although a 'ppstream' did appear under my 'applications' tab on the panel, clicking on it produced nothing. also, after a while, a dialog box appeared warning that i have 1 broken dependency. so i ran the update manager again, and got this error:

```

E: Unable to correct missing packages

W: Failed to fetch http://mirror.nttu.edu.tw/ubuntu/pool/universe/q/qt4-x11/libqt4-test_4.4.0-1ubuntu5~hardy1_i386.deb
  Connection failed


W: Failed to fetch http://mirror.nttu.edu.tw/ubuntu/pool/universe/q/qt4-x11/libqtgui4_4.4.0-1ubuntu5~hardy1_i386.deb
  Connection failed

```

these 2 packages are the same ones that could not install initially, so i guess they are causing the problems. any ideas?

---

### Post by davidmohammed on 2010-12-26
try changing your software software location (administation - software sources - clicking Download From and choosing a different location.

e.g. [this]("http://mosel.estg.ipleiria.pt/mirror/distros/ubuntu/archive/pool/universe/q/qt4-x11/") mirror contains your missing packages

alternatively - just download the missing debs from that location above.

you can install manually

e.g.

cd Downloads

sudo dpkg -i <name of deb>

---

### Post by ubun_tut on 2010-12-27
after i downloaded those 2 packages from your link and installed with the command, i ran update manager again, and managed to get pps running! thanks!

however, although i am able to load the list of channels/movies, i could not play any of the movies that i tried. all of these attempts ended in the pps still downloading the movies. i can try pps on my windows pc (where pps worked fine as of last i tried) to see if its because the pps server is overloaded, but is there a way to check if there are any problems with the pps on my ubuntu?

---

### Post by ubun_tut on 2011-01-01
ok, the pps is not working on my ubuntu. although it is able to display the movie list, when i click on anyone of them to play, it buffers till 100%, then nothing happens. this is the same for all the 10 plus movies that i have tried.

---

### Post by vcrpex on 2011-04-12
hi,
saw that you are having problems with ppstream previously. this thread is abit old. I followed the steps at the website below and it work for my 64bit maverick. i tried method 2 for the installation. Only thing is that this is in chinese, if you are using ppstream, high chances you can read chinese too.

[http://www.dotblogs.com.tw/bowwowxx/archive/2010/12/31/20502.aspx](http://www.dotblogs.com.tw/bowwowxx/archive/2010/12/31/20502.aspx)

hope this helps you. you might probably figure it out already.

---

