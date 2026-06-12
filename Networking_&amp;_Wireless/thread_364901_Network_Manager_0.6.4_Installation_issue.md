---
title: "Network Manager 0.6.4 Installation issue"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Blueshift on 2007-02-18
Hi all!

I had some trouble getting the 0.6.3 release working via the Ubuntu repository (might try again after a clean install), so decided to go ahead and try to compile the 0.6.4 from scratch and maybe get a better result. Unfortunately there are a lot of obstacles on the road to get the darn thing working... I have made the following procedure list:

NetworkManager 0.6.4 Installation on Ubuntu Edgy

Download tarball from [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/)
Expand the tarball
First install the following packages
libiw-dev
libdbus-glib-1-dev
Run ./configure in the libary where the files was expanded to

MAJOR ISSUE: Can't locate hal even though its added in the repository :-(
-----------------------------------
Next milestone
make check
make install
-----------------------------------
Now the configure script tells me that I can try to edit some other file to change the destination of hal, unfortunately I have no idea where hal's precise location is on the hard drive. I am hoping that someone out there might be having better luck installing the 0.6.4 release and could give some pointers....

Thnx in advance! :popcorn:

---

### Post by sillyxone on 2007-02-21
I am able to compile it but it took a few trips back and forth Synaptics to install dependency. I has one problem though: has to start it manually each time (sudo NetworkManager)

Just to make it clear: you have libhal-dev installed?

---

