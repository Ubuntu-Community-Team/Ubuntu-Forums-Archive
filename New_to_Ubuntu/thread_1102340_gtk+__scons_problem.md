---
title: "gtk+ / scons problem?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by sebrofm on 2009-03-21
Hey, i'm trying to install linuxdcpp, but i'm getting an install error when i'm running scons that says gtk+ is missing

Operations:
sudo apt-get install subversion
svn checkout [http://svn.gnome.org/svn/gtk+/trunk](http://svn.gnome.org/svn/gtk+/trunk) gtk
svn checkout [http://svn.gnome.org/svn/glib/trunk](http://svn.gnome.org/svn/glib/trunk) glib
cd path/to/linuxdcpp
scons --help
output:
..~/linuxdcpp-1.0.3$ scons --help
scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.10... no
	gtk+ >= 2.10 not found.
	Note: You might have the lib but not the headers


Any ideas why gtk+ isn't showing up?

thanks!

---

### Post by anewguy on 2009-03-21
Just use synaptic package manager and install GTK and also the GTK development library:

libgtk2.0-bin
libgtk2.0-cli
libgtk2.0-common
libgtk2.0-dev


If you are using C++, Java, etc., there are also libs for those in synaptic package manager.

Dave :)

---

