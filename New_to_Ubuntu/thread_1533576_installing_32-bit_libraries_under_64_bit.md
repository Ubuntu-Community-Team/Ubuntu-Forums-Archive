---
title: "installing 32-bit libraries under 64 bit ?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by dinofelis on 2010-07-18
Hello,

I have the following problem.  I want to use a scientific application (Garfield) which is full of fortran legacy code.  The available executables for linux need shared libraries (g2c) which are not compatible with the gcc version 4 suite as far as I understand.  The general advice was to recompile the application.

After some effort finally I succeeded in recompiling the application under a 32-bit ubuntu (lucid), and it works perfectly, not needing the g2c library anymore.
However, I also need this application to run on a 64-bit system (ubuntu - lucid).  And here is the problem: the code seems to be written for 32 bit systems (in the makefile there is a -m32 option for the compiler).
When I leave that out, everything compiles, but the application itself doesn't run correctly, complaining about 64 bit and 32 bit issues and stops by itself.  
When I take my 32-bit compiled application on the 32-bit system, and just take it to my 64-bit environment, certain shared libraries (cernlib) installed on the system are not found because of 64/32 bit incompatibility.

So my question is: as visibly this code is not 64-bit compatible (probably due to dirty memory tricks in the fortran code), is it possible to install, on a 64-bit system, somewhere 32-bit shared libraries to run this application in its 32-bit version ?

(and this, without screwing up my 64 bit environment in general).

thanks.

---

### Post by wojox on 2010-07-18
Try searching Synaptic for *ia32-libs* or [GetLibs]("http://ubuntuforums.org/showthread.php?t=474790")

---

### Post by sisco311 on 2010-07-18
> **dinofelis said:**
> 
So my question is: as visibly this code is not 64-bit compatible (probably due to dirty memory tricks in the fortran code), is it possible to install, on a 64-bit system, somewhere 32-bit shared libraries to run this application in its 32-bit version ?


Yes, install ia32-libs or create a 32-bit chroot.


If the 32-bit installation is on the same computer, then you could chroot into that.

---

### Post by dinofelis on 2010-07-19
Brilliant !

Thanks a bundle.  With getlibs, I could install everything and the 32-bit version is now up and running on my 64-bit system.

One little caveat: getlibs didn't do it by itself.  In fact, each time I had to run the executable, find out which library was missing, find out with synaptic to which package that library belonged, and then run 
getlibs -p {packagename}
This DIDN'T download the package, but rather, I got something like:

```

me@mymachine:~/garfield9_32.d$ getlibs -p libgfortran3
The following i386 packages will be installed: libgfortran3
Continue [Y/n]? Y
Downloading ...
Failed to download file http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/g/gcc-4.4/libgfortran3_4.4.3-4ubuntu5_i386.deb

```

I then downloaded the package by hand (using firefox), and then installed the package with getlibs -i {packagename}

Maybe this has something to do with the fact that we use a proxy ?

But nevertheless, installing 3 or 4 libraries that way permitted me to have the application up and running.  So thanks a bundle, and thank you very much for getlibs.

cheers!

---

