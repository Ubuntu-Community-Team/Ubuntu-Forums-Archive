---
title: "Aurora Engine Not Working Properly"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by mwgriffin on 2009-07-19
Ok so I had a couple themes that needed the aurora engine to work properly so I followed this guide:
 
----------------------------------------
If you've been browsing through the themes available for Ubuntu, you'll have noticed that quite a few of the better ones require a theme engine called Aurora.
This tutorial will take you through the process of compiling and installing Aurora on Ubuntu so you can use these themes.
Firstly, open a Terminal window and make sure you've got root permissions:


$ sudo bash

Then lets install some prerequisites:


$ apt-get install build-essential auto-apt checkinstall libgtk2.0-dev

Create a source folder in which to compile Aurora.


$ mkdir /src
$ cd /src

Now lets download and extract Aurora 1.5:


$ wget [http://gnome-look.org/CONTENT/content-files/56438-aurora-1.5.1.tar.bz2](http://gnome-look.org/CONTENT/content-files/56438-aurora-1.5.1.tar.bz2) 
$ tar -xvf 56438-aurora-1.5.1.tar.bz2

If this doesn't work (probably due to a new release), get the latest file from [here]("http://gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438").
Extract the Aurora engine:


$ tar -xvf aurora-gtk-engine-1.5.tar.gz

Now change into the Aurora folder and compile:


$ cd aurora-1.5/
$ ./configure --prefix=/usr -enable-animation; make; make install

To install the Aurora theme, open the Aurora.tar.bz2 file in the /src folder with the Appearance manager.
References:
[LIST]
[*][http://gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438]("http://ubuntuforums.org/showthread.php?t=778611")
[*][http://ubuntuforums.org/showthread.php?t=778611](http://ubuntuforums.org/showthread.php?t=778611)
[/LIST]
-------------------------------------------
All seemed to work accordingly until I pulled up synaptic package manager and I immediately noticed that it wasn't skinned.  What it looked like instead was the way that windows 98 looks or how linux looked without the modern gui tools now being used.  I checked other applications and I noticed that many of the system tools were not being skinned.  I thought that this was very strange as I had installed the aurora engine on another ubuntu setup and it didn't have the same issue.  I tried many themes that needed the aurora engine and they all had the same problem, I turned off then turned on my computer to no avail as well as switched the window manager on and off.  Please help if you can.  I'm completely lost.  I also uninstalled and then reinstalled the engine but that didn't help.  I will try again tonight and I will post the result of the uninstallation and installation process.  Thank you!
 
Mike

---

### Post by Tibuda on 2009-07-19
There's a [deb package]("http://gnome-look.org/content/show.php/Aurora+Gtk2+Engine+para+Debian?content=99846") for the Aurora Engine in Gnome-Look. A lot better than compiling source code.

---

### Post by mwgriffin on 2009-07-19
Great!  That is what I wanted to do in the first place.  I just couldn't find one.  I'll let you how that works.  That then brings up my other question.  Can I just uninstall those other applications that I installed by doing $ apt-get install build-essential auto-apt checkinstall libgtk2.0-dev  ?  Because I would like to not have any packages that I don't need on my system.  Will those packages just show up in the synaptic package manager so I can just uninstall them that way?  Or would I call  $ apt-get uninstall build-essential auto-apt checkinstall libgtk2.0-dev  ?  Either way I would like to make sure that I don't have any clutter.  Thank you so much!
 
Mike

---

### Post by Tibuda on 2009-07-21
These packages are used for compiling, so you won't need them for your daily tasks, unless you are a programmer. To uninstall them, you don't use "apt-get uninstall" but "apt-get remove":

```
sudo apt-get remove build-essential auto-apt checkinstall libgtk2.0-dev
```

You can also use synaptic package manager (in system > administration) instead of a terminal if you want to.

---

