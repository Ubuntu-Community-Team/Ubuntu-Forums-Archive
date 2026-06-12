---
title: "Libgpod-0.7.2 installation problems"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by scream_sayonara on 2009-04-24
I am trying to set up my 4th gen 8gb ipod nano to use with amarok in ubuntu intrepid.

I had the usual problem where i can put the files onto the ipod and play them back through amarok etc, but when the ipod is disconnected, it shows no music.

So i am trying to install libgpod-0.7.2, i have downloaded the tar.gz and used the file-roller to extract it into a directory, but when i try to compile it in the terminal, some things go wrong.

after typing the ./configure command, a lot of things happen, but at the bottom it says this: 

checking for LIBXML... configure: error: Package requirements (libxml-2.0) were not met:

No package 'libxml-2.0' found

I'm not sure if this important.. but i tried "make" anyway. And i get this..

screamsayonara@screamsayonara-laptop:~/Desktop/libgpod-0.7.2$ make
make: *** No targets specified and no makefile found.  Stop.

Do i need to.. "specify a target"? Are the files in the directory that are labelled 'Makefile.am' and 'Makefile.in' not the files it is looking for?

Or is there another way to install this libgpod?

---

### Post by scream_sayonara on 2009-04-24
i mean, is it maybe that the archive has something wrong with it?

---

