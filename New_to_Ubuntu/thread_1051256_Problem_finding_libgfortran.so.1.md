---
title: "Problem finding libgfortran.so.1"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by WylieE on 2009-01-26
Hi,
 I recently updated to 8.10 and now am unable to run the statistical package R. 

When I try to run R I get the following: 

 error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

I looked for any libgfortran files and I only have libgfortran.so.2 (or 3 or others, but no 1).  I tried to link libgfortran.so.1 to libgfortran.so.2.  When I do this, I am able to run R, but get this warning message:

 unable to load shared library '/usr/local/lib64/R/library/stats/libs/stats.so':
  /usr/local/lib64/R/library/stats/libs/stats.so: undefined symbol: _gfortran_copy_string

I tried uninstalling and installing R and gfortran (in various orders)  I think I have backports selected (but I'm not positive).
It seems like there is a specific requirement for libgfortran.so.1, but I can't find where this file is available. 
Or is this something simple and I just have my paths messed up ?

Sorry if this is an obvious problem, I'm reminded of my inabilities every time I try to upgrade.  I would appreciate any suggestions on fixing this.

I believe there is a similar problem here :
[http://ubuntuforums.org/showthread.php?t=1049399&highlight=libgfortran.so.1](http://ubuntuforums.org/showthread.php?t=1049399&highlight=libgfortran.so.1)
but still no answers to that one either.
Thanks.

Also, I tried installing ppu-gfortran and adding that to the path:
Then when I try to run R I get this error:
 error while loading shared libraries: /usr/lib/libgfortran.so.1: ELF file data encoding not little-endian

---

### Post by snova on 2009-01-26
You could try installing the Hardy package: [http://packages.ubuntu.com/hardy/libs/libgfortran1](http://packages.ubuntu.com/hardy/libs/libgfortran1)

---

### Post by WylieE on 2009-01-26
Hi,
 Thanks for your response!

> **snova said:**
> You could try installing the Hardy package: [http://packages.ubuntu.com/hardy/libs/libgfortran1](http://packages.ubuntu.com/hardy/libs/libgfortran1)

I tried to install this as:
sudo apt-get install gcc-4.1-base
it says this is the newest version.

If I try to install this file using the package installer it says:
Error: a later version is already installed.

Is there a way to force it to install this version?

I also tried:

> root@colleen:/usr/lib/R# apt-get install libgfortran1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgfortran1: Depends: gcc-4.1-base (= 4.1.2-21ubuntu1) but 4.1.2-23ubuntu3 is to be installed

Thanks again for taking the time to help.

---

### Post by WylieE on 2009-01-26
Well, it may have been a very stupid error. 
And I don't know what I did wrong, but I was able to get R running another way:

Instead of using the binaries available from R, I downloaded the latest release and compiled it.
This works great.

Thanks for the help.
Colleen

PS will someone tell me how to change the thread to solved?
Thanks.

---

### Post by snova on 2009-01-27
> **WylieE said:**
> PS will someone tell me how to change the thread to solved?
Thanks.

Ordinarily it's under Thread Tools, but it's been temporarily disabled. See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

### Post by WylieE on 2009-01-27
OK, Thanks!

---

### Post by samk77 on 2009-12-18
Hi All, 

I have a similar issue with libgfortran.so.3.

I have my C++ executable which throws a similar error message but not on all linux machines. It works well on a few. Below is the exact message:

"../Workspace/setdr: error while loading shared libraries: libgfortran.so.3: cannot open shared object file: No such file or directory".

Is this because the linux machine which throws this message doesn't have the latest fortran library? If so, is there a way to include these libraries in the executable so that the user doesn't have to download the latest files on his linux?

Thanks in advance,
Kiran

---

### Post by samk77 on 2009-12-28
Thank you all. Found a temporary, stealthy way of doing it.
I am including all the shared library files along with the executable that I am going to distribute and temporarily appending its path to LD_LIBRARY_PATH.

---

