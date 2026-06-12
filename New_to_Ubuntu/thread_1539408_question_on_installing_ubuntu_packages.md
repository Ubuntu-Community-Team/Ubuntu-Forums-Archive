---
title: "question on installing ubuntu packages"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-07-26
I had a question about installing Ubuntu packages/libraries manually. Now suppose I want to install package X. Say I download the X.tar.gz file to my desktop and extract the X folder to my Desktop. 
Now I do the usual ./ configure, make and make install steps.  Does the software package get installed in "standard position"(whatever that means) ?

I am asking this question because of the paragraph in bold shown below.


GADGET-2 needs the following non-standard libraries for compilation:
MPI - the Message Passing Interface (version 1.0 or higher). Many vendor supplied versions exist, in addition to excellent open source implementations, e.g. MPICH ([http://www-unix.mcs.anl.gov/mpi/mpich/](http://www-unix.mcs.anl.gov/mpi/mpich/)) or LAM ([http://www.lam-mpi.org/](http://www.lam-mpi.org/)).
GSL - the GNU scientific library. This open-source package can be obtained at [http://www.gnu.org/software/gsl](http://www.gnu.org/software/gsl) , for example. GADGET-2 needs this library for a few simple cosmological integrations at start-up, and for random number generation.
HDF5 - the Hierarchical Data Format. This library has been developed by NCSA and can be obtained at [http://hdf.ncsa.uiuc.edu/HDF5](http://hdf.ncsa.uiuc.edu/HDF5) . GADGET-2 can be compiled without this library, but then the HDF5 format is not supported.
FFTW - the Fastest Fourier Transform in the West. This open-source package can be obtained at [http://www.fftw.org](http://www.fftw.org) . It is only needed for simulations that use the TreePM algorithm. Note that the MPI-capable version 2.x of FFTW is required, and that FFTW needs to be explicitly compiled with parallel support enabled. This can be achieved by passing the option --enable-mpi to the configure script. When at it, you might as well add --enable-type-prefix to obtain the libraries in both a single and double precision version. If this has not been done, you should set the option NOTYPEPREFIX_FFTW in GADGET's Makefile.
**Note that if any of the above libraries is not installed in standard locations on your system, the Makefile provided with the code may need slight adjustments. Similarly, compiler options, particularly with respect to optimisations, may need adjustment to the C-compiler that is used. Finally, theMakefile contains a number of compile-time options that need to be set appropriately for the type of simulation that is simulated.**


Could you also let me know what these standard positions are?

---

### Post by oldos2er on 2010-07-26
If you're installing compiled source code, "sudo make install" usually puts it into /usr/local/bin. Fftw, hdf5, gsl and mpi are all in the repositories though.

---

### Post by natravis on 2010-07-26
To expand on what the previous poster said, if you installed all of the packages from repos, you shouldn't have an issue. If you do, in the makefile there will be a spot asking where each of those programs is installed and we can help you find that out later if needed. Cross that bridge when you get there, etc.

---

