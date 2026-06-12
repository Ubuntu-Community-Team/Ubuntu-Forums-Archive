---
title: "how to install liferea-1.6.5 ???"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by al204 on 2010-12-04
[SIZE=5][SIZE=4]hello everybody,
I downloaded and installed ubuntu these morning 3am and Im starting to download some applications. 
I was able to download liferea-1.6.5, now I need to install it....
what is the easy and simple way to install it?

Among the downloaded files there is a text file with installation instructions....however, they seem a bit complicated....

thanks in advance...

al.
[/SIZE][/SIZE]:razz:[SIZE=5][SIZE=4] 
[/SIZE][/SIZE]

---

### Post by al204 on 2010-12-04
test

---

### Post by anewguy on 2010-12-04
Did you download this via Synaptic Package Manager, or did you download it from another site?

Do the instructions say something like tar, cd to tar'd folder, configure, make and make install?

If you could, attach your installation instructions to a reply here, or at a minimum a link to what you downloaded, and I'll take a look and see if I can help you.

Welcome to ubuntu!

Dave ;)

---

### Post by al204 on 2010-12-04
[SIZE=4]hello all,

this is a copy/paste of one of the sections of the installation document.[/SIZE] [SIZE=4]

is there anything easier? thanks a lot, al[/SIZE] [SIZE=4]

begins here>[/SIZE] [SIZE=4]

Basic Installation[/SIZE] 
==================

These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').

   It can also use an optional file (typically called `config.cache'
and enabled with `--cache-file=config.cache' or simply `-C') that saves
the results of its tests to speed up reconfiguring.  (Caching is
disabled by default to prevent problems with accidental use of stale
cache files.)

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If you are using the cache, and at
some point `config.cache' contains results you don't want to keep, you
may remove or edit it.

   The file `configure.ac' (or `configure.in') is used to create
`configure' by a program called `autoconf'.  You only need
`configure.ac' if you want to change it or regenerate `configure' using
a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

---

### Post by anewguy on 2010-12-04
As I suspected, this is the normal way of package handling in Linux.

Once you downloaded the .tar.gz file, you need to "untar" it - I think the extract option should come up if you just click on the file.  This tells you where it is extracting the files to.

So, normally Ubuntu is going to download files to your userid Downloads folder.  I suspect that when you decompressed the file it created a subfolder of liferead-1.6.5 in your downloads folder - check to be sure.  If so, do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

cd ~/Downloads/liferea-1.6.5 <press enter>

./configure <press enter>  and wait for it to complete

make <press enter> and wait for it to complete

sudo make install <press enter> and wait for it to complete

You may, however, get some errors.  Why?  If you look at the page you downloaded from, it shows some required packages, such as GTK, that must be installed.  You would do best to check these first, install what you need to via Synaptic Package Manager, THEN do the standard configure/make/make install.

Dave ;)

---

### Post by al204 on 2010-12-05
great! thanks a lot! it worked!
as every tutorial I read said....do not expect ubuntu linux to be windows.....and be sure there will be a learning curve.

I used the information you provided plus the Synaptic Package Manager plus some advice from the ubuntu documentation help and it worked. 

I also looked up several unfamiliar terms specific to ubuntu linux like apt, etc.

best regards,

al 

:P:):p

---

### Post by anewguy on 2010-12-05
You're welcome!

If you could take a minute a use the "Thread Tools" option above the first post on the thread and mark this as "Solved", it will help anyone else who may be looking at the same problem.

Hope you enjoy Ubuntu!

Dave ;)

---

### Post by anewguy on 2010-12-05
I should probably add here for you and others, the preferred way of getting applications is via the Ubuntu Software Center or Synaptic Package Manager.  Of course, this isn't always possible, but when it is, please use those methods.  Why?  Both will be sure any dependencies are met (things like GTk, etc., for this package) so you don't try to "make", get errors, download 1 package that was missing, get another error, etc. - the dependencies loop.  It just makes life much easier if you can use those methods.

Dave ;)

---

