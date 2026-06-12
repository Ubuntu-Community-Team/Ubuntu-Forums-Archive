---
title: "WSPR on x64?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by kwacka on 2010-04-11
I've installed WSPR on ASUS EeePC from .deb package at [Princeton.edu/pulsar/K1JT/wspr.html]("http://physics.princeton.edu/pulsar/K1JT/wspr.html") and running fine.

I'm now attempting to get it running on desktop (purely because its running 24/7) but package is for i386 machines only.

Tried installing from source but so many dependencies I surrendered & used dpkg -i --force-architecture wspr_2.00r1714_i386.deb to install.

Unsurprisingly I'm getting an error when I attempt to run - ImportError: /WSPR/WsprMod/w.so: wrong ELF class: ELFCLASS32 - so problems with libraries clearly.

Before I start installing every i386 library that haven't already installed, has anybody successfully got WSPR running on an X64 box?

---

### Post by Didius Falco on 2010-04-11
I'm not running it, but I managed to track down the control file listing here:

[http://svn.berlios.de/svnroot/repos/wsjt/branches/wspr/DEB/DEBIAN/control](http://svn.berlios.de/svnroot/repos/wsjt/branches/wspr/DEB/DEBIAN/control)

according to this document:

> Package: WSPR
Version: 2.00r1682
Section: unknown
Priority: optional
Architecture: i386
Depends: python-tk,python-imaging-tk,python-numpy,libfftw3-3
Maintainer: Joe Taylor, K1JT <k1jt@arrl.net>
Description: Amateur Radio weak-signal communication.


So you could try installing those dependencies and try it out. If that fails, I'd contact Joe Taylor at the email address listed above. He may be able to offer advice, or you may be able to convince him to compile a 64 Bit version available for download.

Good luck with it!!

Regards,

Didius

---

### Post by kwacka on 2010-04-12
Many thanks for the response.

All those dependencies already installed - I'd already installed them via synaptic. When I checked  WSJT (also by K1JT) they use those same libraries so a quick & easy way would be to install WSJT then try WSPR.

Just keep trying, but it seems from various boards that I can also expect audio problems in the future too.

](*,)

---

### Post by Didius Falco on 2010-04-14
When you get it figured out, post the solution in this thread and mark it "solved". Might save someone else's head and/or brick wall. ;)

---

