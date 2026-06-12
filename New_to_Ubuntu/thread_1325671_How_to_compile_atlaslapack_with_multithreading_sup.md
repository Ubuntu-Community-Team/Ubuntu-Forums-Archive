---
title: "How to compile atlas/lapack with multithreading support"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by catzlai on 2009-11-13
I am using ubuntu Karmic and I am trying to install a software called sextractor.
[ftp://ftp.iap.fr/pub/from_users/bertin/sextractor/sextractor-2.8.6.tar.gz]("ftp://ftp.iap.fr/pub/from_users/bertin/sextractor/sextractor-2.8.6.tar.gz")

So I downloaded it and I followed the user manual.
But after I typed ./configure in the terminal I got:
```
checking cblas.h usability... yes
checking cblas.h presence... yes
checking for cblas.h... yes
checking clapack.h usability... yes
checking clapack.h presence... yes
checking for clapack.h... yes
checking for clapack_dpotrf in -llapack... no
checking for cblas_dgemm in -lcblas... yes
checking for clapack_dpotrf in -llapack... no
checking for cblas_dgemm in -lcblas... yes
checking for clapack_dpotrf in -llapack... no
checking for cblas_dgemm in -lcblas... yes
checking for clapack_dpotrf in -llapack... yes
checking for cblas_dgemm in -lcblas... yes
checking for cblas_dgemm in -lptcblas... no
configure: error: CBLAS/LAPack was compiled without multithreading support! Exiting.
```

I have installed liblapack3gf and libatlas3gf-base from the repositories but it seems I need to compile it myself? How do I do it?

---

### Post by catzlai on 2009-11-14
I have sorted out the problem now. For those who need it:

Make sure you have libblas.a and gfortran installed:

```
sudo apt-get install libblas-doc libblas3gf libblas-dev libblas-test gfortran 
```

Download the clapack.tgz and clapack.h from [http://www.netlib.org/clapack/]("http://www.netlib.org/clapack/"), unzip it:
```
gunzip -c clapack.tgz | tar xvf -
```

Place the clapack.h into the clapack folder.

Create make.inc from make.inc.example:
I set ```
RANLIB=echo
``` and ```
BLASLIB=/usr/lib/libblas.a
```

Then ```
make f2clib
sudo make
```

Now download the latest stable version of atlas from [http://sourceforge.net/projects/math-atlas/files/]("http://sourceforge.net/projects/math-atlas/files/")
Unzip it: ```
gunzip -c atlas3.8.3.tar.gz | tar xvf -

```

Create a new folder inside ATLAS, which I named it "linux".

Configure with your own option. Here replace ... with the directory of your CLAPACK. Make sure you have disabled CPU throttling.
```
cd linux
../configure -b 32 --with-netlib-lapack=.../CLAPACK/lapack_LINUX.a
make build
make check
make time
sudo make install
```

Now the libraries should be  at /usr/local/atlas/
=)

So for sextractor,
```
./configure --with-atlas=/usr/local/atlas/lib --with-atlas-incdir=/usr/local/atlas/include
sudo make
sudo make install
```

---

### Post by analalovic on 2009-12-15
:D
Thank you, it saved me a lot of time and prevented a headache. However, I would like to point out 2 things with CLAPACK:
********* I *********  
I had to change paths to folders in files:
CLAPACK-3.2.1/TESTING/LIN/Makefile and CLAPACK-3.2.1/TESTING/EIG/Makefile
from $(F2CLIB) to ../../$(F2CLIB)
from $(BLASLIB)  to ../../BLAS/SRC/$(BLASLIB)
CLAPACK-3.2.1/BLAS/TESTING/Makeblat[1-3]
from $(BLASLIB) to ../SRC/$(BLASLIB)
from $(F2CLIB) to ../../$(F2CLIB)

********* II *********
$ sudo make check 
it will list some 2 errors and this should be ignored as it says itself (I lost some time trying to fix this) 

!!! All Ubuntu users should install embedded atlas, NOT try to download it from somewhere else. I've lost much time to realize this.

If you need PSFEX in addition to SEXTRACTOR, first download it from 

[http://astromatic.iap.fr/wsvn/public/listing.php?repname=public+software.psfex&path=%2Ftrunk%2F#path_trunk_](http://astromatic.iap.fr/wsvn/public/listing.php?repname=public+software.psfex&path=%2Ftrunk%2F#path_trunk_) 

Download all the files you see (in the trunk dir)!!! Move them and unpack in the dir you created called for ex. psfex. 
Then it is only important to configure it well:
$ sudo ./configure --with-atlas=/usr/local/atlas/lib --with-atlas-incdir=/usr/local/atlas/include
$ sudo make 
If it reports a problem in seeing 8 spaces instead of tabs, do 
$ sed -i s/"        "/"\t"/g Makefile
And then 
$ sudo make install

---

