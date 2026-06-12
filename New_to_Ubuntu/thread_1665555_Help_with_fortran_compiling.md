---
title: "Help with fortran compiling?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by cheesewiz27 on 2011-01-12
I post in this forum because I only have limited experience with linux and ubuntu, as I have just now figured out the functionality of the "make" command. If I need to move it somewhere else, let me know.

i have a program called ddscat, which is a discrete dipole approximation program used to simulate the scattering of particles. It is written in Fortran. In its current state, it runs without mpi, and takes a good 2 or 3 days to complete. I want to enable mpi, but am running across problems.

the program comments say to add the following lines to the code:

```
ifdef mpi
      INCLUDE 'mpif.h'
endif
```

however, when I try and go "make ddscat" I get:


```
cpp -P -traditional-cpp -Dmpi -Dopenmp DDSCAT.f90 \
	DDSCAT_cpp.f90
gfortran -c -O2 -openmp DDSCAT_cpp.f90 -o DDSCAT.o
DDSCAT_cpp.f90:35: Error: Can't open included file 'mpif.h'
```

I've installed the packages for gfortran, OpenMPI, and OpenMP. I dont know if those are the right ones, so if I need something else let me know.

I've been searching around for a solution, but I cant get anything to work. The people responsible for the program are not very responsive, so any kind of help would be appreciated.

---

### Post by gmargo on 2011-01-12
You can use the [packages]("http://packages.ubuntu.com/") web site to find all packages with a "mpif.h" file:

[http://packages.ubuntu.com/search?searchon=contents&keywords=mpif.h&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=mpif.h&mode=exactfilename&suite=maverick&arch=any)

I suspect you need to install the [libopenmpi-dev]("http://packages.ubuntu.com/maverick/libopenmpi-dev") package.

---

