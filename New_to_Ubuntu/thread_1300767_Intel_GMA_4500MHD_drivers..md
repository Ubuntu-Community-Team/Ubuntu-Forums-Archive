---
title: "Intel GMA 4500MHD drivers."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by videa on 2009-10-25
Hi guys,

I just installed Xubuntu 9.04 to my laptop with Intel GMA 4500MHD gfx. It didn't automatically install drivers to the chipset, and I would like to install them. 

I downloaded the 2D driver from [http://intellinuxgraphics.org/2009Q3.html](http://intellinuxgraphics.org/2009Q3.html) (Is this the right driver to download?), but I'm total noob to unix systems, and after googling I still have no idea how to actually install them. 

I would really appreciate if someone could tell step to step how to do it. Thank you in advance.

edit. the main reason for installing the drivers is to correct the resolution from 1024x768 to 1280x800 which ain't available now.

---

### Post by dv3500ea on 2009-10-25
Is there a version you can install from the repositories with the package manager (system->administration->package manager)? This would be preferable. Otherwise I suspect what you have is a source package which you need to extract and in a terminal run ```

cd [path to extracted package folder]
make
sudo make install

```.
I am not at all positive this will work but it is worth a try.
See if you can find the documentation for how to install.

---

### Post by videa on 2009-10-25
I have the extracted folder xf86-video-intel-2.90. When typing sudo make install, it just prints "make: *** no rule to make target 'install'. Stop."
In synaptic package manager, I couldn't get it work either. I tried to "add downloaded packages", and tried to quicksearch but with no results.

The folder includes following files:

XX:~/Desktop/xf86-video-intel-2.9.0$ lsvidea> 
aclocal.m4    config.h.in   COPYING     m4           missing   shave-libtool.in
AUTHORS       config.sub    depcomp     Makefile.am  NEWS      src
compile       configure     install-sh  Makefile.in  README    uxa
config.guess  configure.ac  ltmain.sh   man          shave.in

---

### Post by dv3500ea on 2009-10-25
what does README say?

---

### Post by videa on 2009-10-25
> **dv3500ea said:**
> what does README say?


There's no installation instructions..
[I]
Where to get more information about the driver
----------------------------------------------
The primary source of information about this and other open-source
drivers for Intel graphics is:

    [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

Documentation specific to the xf86-video-intel driver including
possible configuration options for the xorg.conf file can be found in
the intel(4) manual page. After installing the driver this
documentation can be read with the following command:

    man intel[/I]

Couldn't find instructions from the web site mentioned neither.

---

### Post by videa on 2009-10-25
I typed sudo "apt-get install xf86-video-intel-2.9.0" to the terminal and booted, and it started working.

Thanks for the help dv3500a.

---

### Post by Braveheart1980 on 2009-12-13
> **videa said:**
> I typed sudo "apt-get install xf86-video-intel-2.9.0" to the terminal and booted, and it started working.

Thanks for the help dv3500a.

Which repo are you using?

---

### Post by 3rdalbum on 2009-12-13
The Intel graphics driver is already preinstalled and enabled where appropriate in Ubuntu (except if you use the latest Poulsbo chipset for netbooks). Your command would have done nothing anyway as there's no package by that name, and you already had the driver. No idea why it wouldn't let you choose the resolution you wanted the first time, though.

---

