---
title: "Glib and Gtk"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by birkopf on 2011-08-15
Please help wit this issue. It's one of the most frequent problems for users who want to compile under ubuntu. 

Gtk and Glib is required to compile lots of software. For some reason I don't have it as a part of my Natty. Going to [http://www.gtk.org/](http://www.gtk.org/) gives me opportunity to download all necessary files and great advise:
```
 
"Where can I use it?
Everywhere!" 

```
But thats about it. Trying to compile those packages:
GTK+ 3.0
GLib 2.28
Pango 1.28
Gdk-Pixbuf 2.22
ATK 1.30

Give another error. Cannot even compile one as it require others and other require external libraries and it just goes on and on!

Can someone help me (in clear language) so that this post can stay as a direction for other users on Glib and GTK issue please?

---

### Post by Bachstelze on 2011-08-15
If you want to compile software that uses a library, you need the development files for that library. In general they are in the package libsomething-dev.

---

### Post by birkopf on 2011-08-15
> **Bachstelze said:**
> If you want to compile software that uses a library, you need the development files for that library. In general they are in the package libsomething-dev.

Thanks for answer Bachstelze but that's pretty much what I already know. Choppy road starts after that... 

glib and gtk is required for almost everything but it's dependencies and complications (for novice/normal user) are vast... 

Still no chance with my problem :*(

---

### Post by Bachstelze on 2011-08-15
Ask a more precise question, then. What exactly are you trying to do and what exactly is the problem?

---

### Post by birkopf on 2011-08-16
> **Bachstelze said:**
> Ask a more precise question, then. What exactly are you trying to do and what exactly is the problem?

All my questions are in first post.
Shall I write in bullet points? OK:

- Why on standard ubuntu installation there isn't Glib and Gtk (and gtk.h) installed ?
- How to have it installed ?

---

### Post by anewguy on 2011-08-16
Try using the synaptic package manager -

- the development library for glib is there - in 10.10 it is libglibmm-2.4-dev, and when you select it the package manager comes up with it's dependencies that it will automatically install

- similary, the GTK development libs are also there, and when selected the package manager automatically installs their dependencies

Why aren't they install by default?  I've written C programs using GTK, but I think you'll find they aren't included as they are DEVELOPMENT libraries, not run time libraries.  The run-time libraries are already there so you can EXECUTE GTK, etc., programs.  When you want to develop programs using some framework you have to expect to install the libraries needed.

USE Synaptic Package Manager to install such things - you'll get the dependencies then automatically.  Some say apt-get does too, but I've been burned in the past by it not installing dependencies.  Perhaps that is fixed - I don't know, and I'm not saying so to start a p***ing contest about apt-get.  Just use the package manager - you'll see when you select a package the additional packages (e.g. dependencies) that will also be installed.  These may not be the most current according to sites like gtk.org, but they are the ones known to work with a given release of ubuntu.  You don't have to download and compile the libs - just use the package manager.  Need lib pango for development?  It's there as well.

---

### Post by anewguy on 2011-08-16
> **birkopf said:**
> All my questions are in first post.
Shall I write in bullet points? OK:

- Why on standard ubuntu installation there isn't Glib and Gtk (and gtk.h) installed ?
- How to have it installed ?

And.....people with vastly more experience have been trying to help you - watch your attitude.  If you've done it already, then obviously you don't know what you're doing.

---

### Post by birkopf on 2011-08-16
> **anewguy said:**
> 
- the development library for glib is there - in 10.10 it is libglibmm-2.4-dev, and when you select it the package manager comes up with it's dependencies that it will automatically install


OK. Found this now after full file name. 


> **anewguy said:**
> 
- similary, the GTK development libs are also there, and when selected the package manager automatically installs their dependencies


- Do you have by chance a filename of gtk like this one above ? Nothing comes up when I search for GTK or gtk dev ? 

- Or is it this one: libgtk-3-dev ?
It's confusing as in Synaptic there are hundreds of packages for GTK (graphical look of desktop)


> **anewguy said:**
> 
Why aren't they install by default?  I've written C programs using GTK, but I think you'll find they aren't included as they are DEVELOPMENT libraries, not run time libraries.  The run-time libraries are already there so you can EXECUTE GTK, etc., 
 

Ok. Logic. If you want to develop and compile you'd need development libraries. It could be included in build essential... but isn't. Anyway - wouldn't be an issue if there will be some howto in the net. So many people was asking... 


> **anewguy said:**
> 
USE Synaptic Package Manager to install such things - you'll get the dependencies then automatically.  Some say apt-get does too, but I've been burned in the past by it not installing dependencies.  [cut] 


I always use synaptic. Not only I have dependencies, but also full properties and most important - History - to track changes in the system. One of the best paying practices I learned over the years on Linux :)

---

