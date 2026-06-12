---
title: "How to install R-2.10.1"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by rohit raj on 2010-07-07
I am following instructions given in Read me. 

First step is to run ./configure 

I run it, but it fails, what can i do to proceed

Following is output of ./configure

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
loading site script './config.site'
loading build-specific script './config.site'
checking for pwd... /bin/pwd
checking whether builddir is srcdir... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for gawk... gawk
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking for ar... ar
checking for a BSD-compatible install... /usr/bin/install -c
checking for sed... /bin/sed
checking for less... /usr/bin/less
checking for perl... /usr/bin/perl
checking whether perl version is at least 5.8.0... yes
checking for gtar... no
checking for tar... /bin/tar
checking for dvips... no
checking for tex... no
configure: WARNING: you cannot build DVI versions of the R manuals
checking for latex... no
configure: WARNING: you cannot build DVI versions of all the help pages
checking for makeindex... no
checking for pdftex... no
configure: WARNING: you cannot build PDF versions of the R manuals
checking for pdflatex... no
configure: WARNING: you cannot build PDF versions of all the help pages
checking for makeinfo... no
configure: WARNING: you cannot build info or HTML versions of the R manuals
checking for texi2dvi... no
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for gzip... /bin/gzip
checking for bzip2... /bin/bzip2
checking for firefox... /usr/bin/firefox
using default browser ... /usr/bin/firefox
checking for acroread... no
checking for acroread4... no
checking for xdg-open... /usr/bin/xdg-open
checking for pkg-config... /usr/bin/pkg-config
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking how to run the C preprocessor... gcc -E
checking for gfortran... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking for ftn... no
checking for g95... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for fc... no
configure: error: No F77 compiler found

---

### Post by jtarin on 2010-07-07
[Look to here]("http://cran.r-project.org/doc/FAQ/R-FAQ.html#Are-there-Unix_002dlike-binaries-for-R_003f") and scroll down to "2.6 Are there Unix-like binaries for R?"

---

### Post by timbosity on 2010-07-07
latest R is 2.11.1. Is there a reason you want 2.10?

I think the ubuntu repositories have R so you can just install R with ```
sudo apt-get install r-base-core
```

Else, if you want to compile from source (as you seem to be trying to do), you'll need all the dependencies, which from the output you posted is being hung up by no fortran 77 compiler (configure: error: No F77 compiler found).

So you can either try and fulfill those dependencies yourself (by installing an F77 compiler) or simply installing binary from repositories.

---

