---
title: "trying to get my bluetooth headphones to work"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by pacobuntu on 2009-07-05
I am trying to get my headphones to work there is another thread on this but it wont let me post on that thread for some reason.  The how to includes this :
-----------------------------------------------------------------------------------------------------------------

After the installation of all packets, the sources have to be downloaded and compiled. These commands have to be executed in a root-shell:

$ cd /usr/src
$ cvs -d: pserver:anonymous@cvs.sf.net:/cvsroot/bluetooth-alsa co btsco
$ cd btsco
$ ./bootstrap
$ ./configure
$ make
$ make install
$ cd kernel
$ make
$ make install

-------------------------------------------------------------------
but I dont understand any of this, where do I download those sources, and how do I complile them, and how do I execute them in a root shell??????

I know this is a HUGE can-o-worms especially since I have no experience at all in using command line in any OS.  I know NOTHING so please be exact and from the first action needed from desktop.  Your patience will be VERY appreciated and someday when I do understand more I will be happy to be as generous.  I just want to do the things I love to do and be free from the OS monsters out there and someday know enough to help others.

THanks!!!!!!!!!!!1

---

### Post by Boondoklife on 2009-07-05
Are you running 9.04 and fully updated?

---

### Post by pacobuntu on 2009-10-19
Sure am! thanks for getting back to me.  Sorry I haven't been back to this post in a while. I've had other things suck up my time but I'd still like to get this one fixed up.

---

### Post by Boondoklife on 2009-10-19
Well easiest solution I have seen is just use Karmic, the bluetooth headphones just work with that.

---

### Post by pacobuntu on 2009-11-19
Just did, and it works great!  then my DVD burner died right after my update and doesn't even work in WinD'ohs

---

### Post by Boondoklife on 2009-11-19
damned if you do and damned fi ya dont somedays it seems =P

---

