---
title: "OpenMCU Broken"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by vjason on 2007-11-21
I am working to build a H323 video conferencing server based on Ubuntu.  I have found OpenMCU non fuctioning, meaning it will run but will not mix video or audio.  I have found an extreme lack of documentation on OpenMCU in general.  Another thing I have found is the install package does not install the man pages correctly nor does it install the default openmcu.ini files.  If anyone has any guidance it would be appriciated.

---

### Post by trepje on 2007-12-12
The version installed using apt-get isn't in full working order (2.1 I think)

Version 2.2.1 works... only problem is you will have to download and compile - which means compiling pwlib+openh323+openmcu.

A good place to start is [http://www.voxgratia.org/downloads.html](http://www.voxgratia.org/downloads.html)
If you need h.263 (e.g. for netmeeting) [http://www.voxgratia.org/docs/h263_codec.html](http://www.voxgratia.org/docs/h263_codec.html)
I had to edit a couple files to get it to compile:

openmcu/filemembers.h I had to add #include <deque>
openh323/includes/ixjlid.h removed #include <linux/compiler.h>

For the man page gzip the openmcu.1 file and stick it in /usr/share/man/man1/
It explains about the web interface on port 1420 which creates the openmcu.ini file automatically.

---

