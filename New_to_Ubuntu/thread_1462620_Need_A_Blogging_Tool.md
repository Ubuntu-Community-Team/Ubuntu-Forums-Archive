---
title: "Need A Blogging Tool"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by jaco223 on 2010-04-25
Hey Everyone

I'm trying to find a good blogging tool for Ubuntu. I  tried using BloGtk, I've installed
it, but it won't run. When I try to run it from the menu it looks like it is going to start up
then it just craps out.

I've also tried to execute it from the command line and I got this:

jaco@ubuntu:/usr/bin$ ./blogtk 
Traceback (most recent call last):
  File "./blogtk", line 14, in <module>
    import gtkhtml2
ImportError: No module named gtkhtml2

I don't know how to proceed from here. Any help is greatly appreciated!

Jaco

---

### Post by bville09 on 2010-04-25
It looks like it's one of those "module is installed, but python doesn't want to read it" errors, based on similar posts on google.

I haven't tried these, but they might be what you're looking for:

gnome-blog
(can post directly from the panel, seems to work with most sites such as blogspot and blogger)
[http://projects.gnome.org/gnome-blog/](http://projects.gnome.org/gnome-blog/)

Drivel
(seems like the best gnome alternative to BloGTK)
[http://sourceforge.net/projects/drivel/](http://sourceforge.net/projects/drivel/)

---

### Post by Temposs on 2010-04-25
Did you install that application from the Ubuntu Software Center? That kind of error really shouldn't have happened if you did.

If you want to keep trying to use that app, you can fix that error by going to System->Admin->Synaptic Package Manager, and install the python-gtkhtml2 package.

---

### Post by jaco223 on 2010-04-30
I installed Blogtk 2.0, and seem to have all the dependency installed, and it shows up in >Applications>Internet, and I execute the program it starts up ok, but the cursor just keeps spinning and says blogtk2 starting, it just kind of spins for like 15 or 20 seconds, after that the program is fine, It's really annoying and I don't think it should start up this way. Anyone else ever use this program? I'm running Lucid 10.04. This program depends on python, and as far as I know I have all the python libraries installed. Any help is greatly appreciated. Thanks

Jaco

---

### Post by jaco223 on 2010-04-30
Here's a screenshot of what I'm talking about. You can't see the cursor, but it just spins and you can't use the program until it stops spinning.

---

### Post by jaco223 on 2010-04-30
the only way it works correctly is if I leave it in the folder I downloaded and extracted the program in which is /home/jaco/Downloads/blogtk-2.0. I'm stumped.

---

### Post by topdownjimmy on 2010-05-12
> **Temposs said:**
> Did you install that application from the Ubuntu Software Center? That kind of error really shouldn't have happened if you did.

If you want to keep trying to use that app, you can fix that error by going to System->Admin->Synaptic Package Manager, and install the python-gtkhtml2 package.
I'm also getting this problem after installing from the Software Center.

And I see no python-gtkhtml2 package in Synaptic.

Propose changing this thread title to something like "BloGTK missing dependencies"?

---

### Post by AnneTanne on 2010-06-09
Same here... Installed Blogtk from synaptic.  When it didn't start up, tried to do via Terminal and got the error:
Traceback (most recent call last):
File "./blogtk", line 14, in <module>
import gtkhtml2
ImportError: No module named gtkhtml2

Didn't find something like 'gtkhtml2' in synaptic, so tried to solve the problem by installing libgtkhtml2-0, but nothing...

Searching for a solution, I find postings on the www mentioning this problem as far back [as 2004]("https://lists.ubuntu.com/archives/ubuntu-users/2004-December/019005.html")???  But no solution that works...

---

### Post by BloGTK on 2010-06-15
Ubuntu doesn't have the newest version in the official repositories yet. They're still supplying 1.1, which is now years out of date.

The links in my signature explain how to get the new version, which works in 10.04. I'm going to try to get Ubuntu to package 2.0 shortly so that this problem doesn't keep popping up.

---

