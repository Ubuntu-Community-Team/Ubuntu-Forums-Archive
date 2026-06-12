---
title: "Can't execute certain files from command line"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by men8th on 2009-01-03
Hi

I'm trying to install Sun Studio 12. I have followed the instructions given here:

[http://ubuntuforums.org/showthread.php?t=554514](http://ubuntuforums.org/showthread.php?t=554514)

And now run into a brick wall. The IDE starts OK but then complains that it can't run a file called CC (i.e. the C compiler presumably)

I've opened up a terminal and cd'd to the install directory. Typing ./CC gives the following...

tim@GGEOM:/usr/local/SunStudio12ml-linux-x86-200709-ii/sunstudio12/prod/bin$ ./CC
bash: ./CC: No such file or directory

However, the file clearly is there. Here is an extract of ls -l

-rwxr-xr-x 1 root root   323213 2008-12-31 10:28 cc
-rwxr-xr-x 1 root root   409427 2008-12-31 10:28 CC
-rwxr-xr-x 1 root root   603271 2008-12-31 10:28 CCadmin
-rwxr-xr-x 1 root root  4991543 2008-12-31 10:28 ccfe
-rwxr-xr-x 1 root root   590760 2008-12-31 10:28 CClink
-rwxr-xr-x 1 root root   138971 2008-12-31 10:28 c++filt

A bit more playing reveals that script file in that directory will execute, binaries won't (not an exhaustive test).

Can anyone suggest anything. Do you need any further info.

Thanks in advance, Tim

---

### Post by cmnorton on 2009-01-04
Look in your logs (/var/log) to see if the installation went OK. 

You've peformed the right tests to see why stuff won't run. Those files are marked excutable. 

You can also take this up with the site from which you downloaded the package.

---

### Post by dunkar70 on 2009-01-04
Have you tried executing the file with sudo? The the path listed in step 5 of the instructions for 1) typos and 2) accuracy. Make sure the path on your system is the same as the path assumed in the instructions.

---

### Post by oldos2er on 2009-01-04
Have you installed the package build-essential?

---

