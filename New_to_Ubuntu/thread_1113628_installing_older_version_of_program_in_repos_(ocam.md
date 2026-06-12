---
title: "installing older version of program in repos (ocaml)"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by karasuman on 2009-04-01
I need to get [HOL Light]("http://www.cl.cam.ac.uk/~jrh13/hol-light/") running, which requires Ocaml, but a version prior to 3.10.  The version I find with

```
sudo apt-get install ocaml
```

is version 3.11.

On the [Caml website]("http://caml.inria.fr/pub/distrib/ocaml-3.08/"), I can find older versions of the program.  I downloaded one (I actually tried a few different versions numbers; 3.8.3 and 3.9.3), moved it to the directory where I like to keep such things, extracted the files, and followed the installation instructions:

```
./configure
sudo make world
sudo chmod +xr *
umask 022
sudo make install
```

As far as I can tell, these are all progressing without error.

Then I type

```
ocaml
```

and I'm told that it doesn't exist.

I'd really appreciate any help somehow getting a version of ocaml older than 3.10 working.

---

### Post by mikechant on 2009-04-02
Maybe it's not in your $PATH (a variable which defines what directories to search for executables in).
Try changing directory to the directory where the ocaml executable is installed and running it with ./ocaml

If that works you can set up a launcher for it or add the directory to your $PATH (can be explained if required).

Or maybe it would be better to install to another location in the standard path(anybody got any opinions about this?)

---

### Post by SpenceMakesSense on 2009-04-02
It may help to search caml deb on google.

---

