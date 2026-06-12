---
title: "Install beta Gimp"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by michael.ministry on 2009-12-26
Gimp has a beta version 2.7 
I downloaded the "gimp-2.7.0.tar.bz2"
How do I go about installing it?
I'm a total newby.  I uninstalled the gimp version that came with Ubuntu 9.10

Thanks for any help you can give!

Michael

---

### Post by cbabbage on 2009-12-26
Open a terminal, change to the directory of the GIMP 2.7 files. Then unpack the archive by:

bzip2 -d (archive)
tar -xf (archive)

Now the files will be unpacked. Somewhere there will be a README file, which will tell you which commands to run. You will need to do something along the lines of:

./configure
make
make install

but the README file should tell you specifically what to do.

---

