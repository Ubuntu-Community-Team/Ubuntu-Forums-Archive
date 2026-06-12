---
title: "Download Software"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Roadbloc on 2009-01-27
Is it possible to download software without having the machine you want the software for on the internet. This seems to be the only problem with ubuntu, if it is possible it will be the perfect os. :p

---

### Post by Ben Webber on 2009-01-27
If you are looking for specific packages, you can always try the software project's website and look for **.deb** files to install on your offline Ubuntu computer.

---

### Post by stalkingwolf on 2009-01-27
you could also down load the tarballs and use the dreaded C word.  compile.

There is a site where you can download updates and things to burn on a CD/DVD.  I just cant locate it right now.

---

### Post by mocoloco on 2009-01-27
Yes!
Open synaptic (under System-> Administration).  Mark all the stuff you want to install.  Instead of clicking apply, go to File -> "Generate package download script"
Save the file with any name you want, but give it a .sh extension if you want to run it on another Linux system.  
If you look in the file you'll see it just has urls of all the .deb files, and wget commands to get them all quickly in a script.  If you're going to download them on a windows machine you can do it manually, or you can get [wget for windows]("http://pages.interlog.com/~tcharron/wgetwin.html"), and just rename the file to .bat and run it from a directory with wget in it (or put wget in your path).

Put all your .debs on a USB drive or whatever, then back on your non-connected machine rather than install them manually, just open Synaptic again, go to File -> "Add downloaded packages" and select the folder that contains all your debs.  That's it.

---

### Post by Ben Webber on 2009-01-27
> **mocoloco said:**
> Open synaptic (under System-> Administration).  Mark all the stuff you want to install.  Instead of clicking apply, go to File -> "Generate package download script"
Save the file with any name you want, but give it a .sh extension if you want to run it on another Linux system.  
If you look in the file you'll see it just has urls of all the .deb files, and wget commands to get them all quickly in a script.  If you're going to download them on a windows machine you can do it manually, or you can get [wget for windows]("http://pages.interlog.com/~tcharron/wgetwin.html"), and just rename the file to .bat and run it from a directory with wget in it (or put wget in your path).

That's a great trick!

---

