---
title: "Compiling Audacious 2.1.0 from source - never done before"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-05-23
Hey guys,

I'm trying to compile the new Audacious from source, but I'm absolutely inept at doing that stuff. I'm following the installation instructions, but I already get stuck at the first step: ./configure.

Here are the installation instructions:
=======================================

2. Installation
---------------

Audacious requires the following libraries and their development
packages installed:

  Glib 2.14.0
    [http://www.gtk.org/download/](http://www.gtk.org/download/)

  GTK+ 2.10.0
    [http://www.gtk.org/download/](http://www.gtk.org/download/)

  mcs >= 0.7
    [http://www.atheme.org/projects/mcs.shtml](http://www.atheme.org/projects/mcs.shtml)

  libmowgli >= 0.4
    [http://www.atheme.org/projects/mowgli.shtml](http://www.atheme.org/projects/mowgli.shtml)

  GNU Make >= 3.80

Note that these tools and libraries are bundled with major Linux
distributions. Use the packages provided with them where possible. If
those packages are not sufficiently new, you may need to search
third-party repositories for them.


2.1. Basic Installation
-----------------------

cd audacious-VERSION
./configure
make
make install

This will put the binary in /usr/local/bin and plugins in
/usr/local/lib/audacious/.


Here's the error message I get:
===============================

Cannot find Glib2! If you are using binary packages based system, check that you have the corresponding -dev/devel packages installed.


I use Ubuntu Jaunty 64 bit, I thought this would count as a "major Linux distribution" and thus have all the necessary packages preinstalled. I also cannot find glib on synaptic (well I do find a couple packages that have "glib" in their name, but no idea which ones are the right ones), and when I look online, I find sources for glib, but I'd hate to start compiling all the libraries I need to compile Audacious from source from source. Where does it end?

Perhaps somebody can give me some help, walk me through the thing or point me to a tutorial. I really would like to get that new Audacious running, and there are no packages for it yet.

Thanks!
Matthias.

---

### Post by Mornedhel on 2009-05-23
Hi,

You need to install packages ending in -dev. These provide the headers against which you will compile. You usually do not need these packages unless you want to compile something, which is why standard packages containing only the libraries are also available and installed by default.

The corresponding packages, in your case, should be libglib2.0-dev, libgtk2.0-dev, libmcs-dev, libmowgli-dev, and of course make.

---

### Post by mc4man on 2009-05-23
While you didn't mention what ubuntu version your using, if it's intrepid or jaunty the versions of your dependencies should be ok.
For hardy you'll need to upgrade a couple

Also note that you need to build the plugins source as well as the audacious core.

I'd remove your current audacious and audacious-plugins first

> when I look online, I find sources for glib, but I'd hate to start compiling......

That could prove to be a big mistake, all the glib libraries you need are available from the ubuntu repos for whatever release your using

---

### Post by The Bright Side on 2009-05-23
Thanks! That actually helped a lot. I was able to go through ./configure, make and make install (last one only with sudo), Audacious2 appears in my Sound&Video menu, but it won't run. Here's the message I get in the terminal:

/home/thebrightside/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
audacious2: unable to launch selected interface skinned


Also, the plugins don't have their own readme for installation, and when I try ./configure in the plugins directory, I get the following:

[...]
checking for DBUS... no
configure: error: Cannot find dbus-glib >= 0.60


mc4man, it's Jaunty - yep, removed old Audacious first. Thanks!

---

### Post by mc4man on 2009-05-23
I've got to go to work, probably this (search in synaptic

libdbus-glib-1-dev

(you may find your missing a number of depends for the plugins, read thru your ./configure carefully, even it it succeeds you may be missing plugins you want

I just did on hardy and to note - while almost everything is enabled by default in audacious core, resampling is not.
If you want that option you'll need to enable it (enable-samplerate) and have the -dev (libsamplerate0-dev

That should work ok, I have the latest libsamplerate in hardy(1.7) so can't say for sure

You may find this helpful
```
sudo apt-get build-dep audacious-plugins
```

---

### Post by afrodeity on 2009-07-12
Can one run Glib2 on hardy? Will it slow the system down? If so, where is the ppa for it, because it not in the repo?

---

### Post by Mornedhel on 2009-07-12
> **afrodeity said:**
> Can one run Glib2 on hardy? Will it slow the system down? If so, where is the ppa for it, because it not in the repo?

Yes it is, according to [http://packages.ubuntu.com/hardy/libglib2.0-dev](http://packages.ubuntu.com/hardy/libglib2.0-dev). You're using it already anyway, since many Gnome applications depend on it.

---

