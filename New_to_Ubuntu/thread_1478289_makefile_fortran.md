---
title: "makefile fortran"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Milenkonslisboa on 2010-05-09
I have a source code so.f,input data file results.dat and makefile(which I have written).How to call makefile from terminal?

---

### Post by r-senior on 2010-05-09
It should be as simple as:

$ make

---

### Post by Milenkonslisboa on 2010-05-09
make: *** No rule to make target `so'.  Stop.

---

### Post by Milenkonslisboa on 2010-05-09
# Makefile
FC = gfortran
# flags for debugging or for maximum performance
FCFLAGS = -O3
# List of executables to be built within the package
so: so.o results.dat
$(F77) $(FLAGS) -o so.o
# object files
$(F77) $(FLAGS) -c so.f -o so.o
What is wrong with my makefile?

---

### Post by r-senior on 2010-05-10
Bearing in mind I've never used gfortran (but I've used make with gcc), don't you need a rule to make your .o file? Also the linking phase needs the input file?

```

[COLOR="Silver"]FC = gfortran
FCFLAGS = -O3
[/COLOR]
so: so.o results.dat
    $(F77) $(FLAGS) [COLOR="Red"]-o so so.o[/COLOR]

[COLOR="Red"]so.o: so.f[/COLOR]
    $(F77) $(FLAGS) -c so.f -o so.o

```

The FC and FCFLAGS definitions don't appear to be doing anything? There are probably also default make rules that you can use to simplify the whole thing. And are you sure you want to relink when the .dat file changes?

My make is rusty. Maybe you need to do some reading up on make?

[GNU Make]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=14&ved=0CIkBEBYwDQ&url=http%3A%2F%2Fwww.cl.cam.ac.uk%2Fteaching%2F0910%2FUnixTools%2Fmake.pdf&ei=i9HnS9aHN4ju0gSkktDOBg&usg=AFQjCNHFL7H-itrzENqwJmACGx6FjGg1eA&sig2=HImqFg3CflD_PBf5NUxIFA")

---

