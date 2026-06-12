---
title: "Xautoclick installation"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-10-14
I'm trying to install xautoclick but the terminal keeps giving error messages. I installed the required packages using this command. 
sudo aptitude install g++ xserver-xorg-dev python-gtk2-dev </code><code>

Then, I ran ./configure, as given in the install file in the xautoclick package. 

This is the output I get:
```
 
xyz@xyz-desktop:~/Desktop/xautoclick-0.30$ ./configure
Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... yes (using /usr/include)
Checking for X11 ... yes (using -L/usr/lib -lX11 -lXext)
Checking for XTest extension ... no
X11 found, but it does not seem to have the XTest extension
No X11 dependant applications will be build

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : no
cAutoClick    : no
gAutoClick    : no
gAutoClick2   : no
qtAutoClick   : no
qt4AutoClick  : no
fltkAutoClick : no

Installation prefix : /usr/local

None of the xautoclick applications can be build. You need to install the
development packages of X11, GTK+ and/or QT. Check the documentation of
your distribution for details.


```

---

### Post by kroq-gar78 on 2011-01-23
From what I've read on other posts, you have to install xorg-dev first, so
```
sudo apt-get install xorg-dev
```
and then
```
./configure
```
and then make, sudo checkinstall -D (creates a package so its a LOT easier to remove)

Sadly, when I run make, it gives me some "out of scope" error and then quits, so I can't help you from there.

---

### Post by garliqboy on 2011-12-26
need help with installation. The error i get looks like this:
```
~/Desktop/xautoclick-0.30$ ./configure
Checking for c compiler ... no

Error: can't find compiler

Check "configure.log" if you do not understand why it failed.

```
when i open up the "configure.log", it says 
> ============ Checking for c compiler ============
Result is: no
##########################################

i have done everything that i have seen on forums and suggestions and still get this problem. i have installed and re-installed build-essential. i have gcc 4.6.1. 

does anybody have a solution to this problem? I would deeply appreciate it, because I am getting quite frustrated with this error. I've also tried a few other auto click programs, all to no avail, and xautoclick seems to have the least amount of errors.

---

### Post by disPlay on 2012-03-10
I have the same problem here.

which C compiler I need to use the Xautoclick

---

### Post by Script Warlock on 2012-03-10
> **disPlay said:**
> I have the same problem here.

which C compiler I need to use the Xautoclick [this]("https://launchpad.net/~c-korn/+archive/ppa/+packages") might help you or [this]("http://www.ubuntuupdates.org/package/getdeb_apps/oneiric/apps/getdeb/xautoclick")

---

