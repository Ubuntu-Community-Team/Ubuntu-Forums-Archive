---
title: "make error - libraries not being recognised"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by dave-o-dave on 2010-08-17
Dear all,
I have been looking to solve a problem I installing some software.
Although many similair forums appear to exist, i could not find one for this problem.

I am running ubuntu 10.04 through virtual box hosted by windows XP.
I am using a laptop, hp elitebook2530p. 

When I try to compile my software (Gate_v6.0.0) I receive the following error message:


```
Linking Gate
/usr/bin/ld: cannot find -lCore
collect2: ld returned 1 exit status
make: *** [bin/Linux-g++/Gate] Error 1

```what I don't understand is that as far as I can tell the library is installed.
here the output from ls /usr/lib/libcore*

```
/usr/lib/libcore++.a         /usr/lib/libcorex++_level1.a         /usr/lib/libcorex++_level2.so        /usr/lib/libcorex++_level3.so.1
/usr/lib/libcore++.so        /usr/lib/libcorex++_level1.so        /usr/lib/libcorex++_level2.so.1      /usr/lib/libcorex++_level3.so.1.0.0
/usr/lib/libcore++.so.1      /usr/lib/libcorex++_level1.so.1      /usr/lib/libcorex++_level2.so.1.0.0
/usr/lib/libcore++.so.1.0.0  /usr/lib/libcorex++_level1.so.1.0.0  /usr/lib/libcorex++_level3.a
/usr/lib/libcore++.so-old    /usr/lib/libcorex++_level2.a         /usr/lib/libcorex++_level3.so

```I found some forums suggesting to remove, and then recreate the symbolic link libcore++.so ,
but this has not resolved the issue. 

Any ideas would be much appreciated.

Thanks,

Dave

---

### Post by Paul820 on 2010-08-17
Yes the libraries are there, but you need the development header files. Look in synaptic for 'libcore' and there should be one with **-dev** at the end, get that one.

---

### Post by dave-o-dave on 2010-08-17
this library package is included. 
although i may have installed too much. 
I tried to install anything with libcore in my earlier desperation.

I attach a screenshot of synpatic to show you what I have installed.

---

### Post by Paul820 on 2010-08-17
Ah, sorry, you do have the development headers. What is gate? Where is the website you download the source from?

---

### Post by dave-o-dave on 2010-08-17
It is a medical imaging simulation package. 
I think you have to register to download it. 
[http://opengatecollaboration.healthgrid.org/](http://opengatecollaboration.healthgrid.org/)

You have to install all kinds of other things first. clhep, geant4, root...
the tar of the source code is too large to attach, (and I am not sure whether it'd be allowed). 
I would be surprised if the problem was there. It is bound to be something I have done.

---

### Post by anglican on 2010-08-17
> **dave-o-dave said:**
> Dear all,
I have been looking to solve a problem I have installing some software.

```
Linking Gate
/usr/bin/ld: cannot find -lCore
collect2: ld returned 1 exit status
make: *** [bin/Linux-g++/Gate] Error 1

```what I don't understand is that as far as I can tell the library is installed.
here the output from ls /usr/lib/libcore*

```
/usr/lib/libcore++.a         /usr/lib/libcorex++_level1.a         /usr/lib/libcorex++_level2.so        /usr/lib/libcorex++_level3.so.1
/usr/lib/libcore++.so        /usr/lib/libcorex++_level1.so        /usr/lib/libcorex++_level2.so.1      /usr/lib/libcorex++_level3.so.1.0.0
/usr/lib/libcore++.so.1      /usr/lib/libcorex++_level1.so.1      /usr/lib/libcorex++_level2.so.1.0.0
/usr/lib/libcore++.so.1.0.0  /usr/lib/libcorex++_level1.so.1.0.0  /usr/lib/libcorex++_level3.a
/usr/lib/libcore++.so-old    /usr/lib/libcorex++_level2.a         /usr/lib/libcorex++_level3.so

```
It may be that the capital 'C' at the beginning of "Core" is your problem. Try making the symlink as libCore - or changing the makefile to a small 'c' as in -lcore.

H

---

### Post by dave-o-dave on 2010-08-17
just tried it , thanks.
didn't seem to help though. 

I only edited the one file libcore++.so - just made a new symbolic link for 
libcore++.so.1.0.0 to libCore++.so 

but after attempting another recompile, I get the same error. 


thanks anyway. 

please keep these ideas coming

---

### Post by anglican on 2010-08-17
> **dave-o-dave said:**
> just tried it , thanks.
didn't seem to help though. 

I only edited the one file libcore++.so - just made a new symbolic link for 
libcore++.so.1.0.0 to libCore++.so 

but after attempting another recompile, I get the same error. 


thanks anyway. 

please keep these ideas comingTry linking to just libCore.so (no "++").

H

---

### Post by dave-o-dave on 2010-08-18
I have just started up to continue looking at this problem and the problem seems to have gone away. 
The error has now moved on to
/usr/bin/ld : cannot find -lCint

so it has moved on to another library (as had happened to me before I posted).
Which genuinely doesn't seem to be in the /usr/lib/ folder. 


Could it be that any of the changes we made i.e. renaming etc required a restart?
Finally, could anyone recommend a website that tells me what the full names of libraries are?


say i am looking for -lCint , but it is called something else in synaptic. 

The only packages that come up in synaptic when i search for cint are 
root-system-bin 
root-system

both are installed.

---

### Post by anglican on 2010-08-18
> **dave-o-dave said:**
> I have just started up to continue looking at this problem and the problem seems to have gone away. 
The error has now moved on to
/usr/bin/ld : cannot find -lCint

so it has moved on to another library (as had happened to me before I posted).
Which genuinely doesn't seem to be in the /usr/lib/ folder. 


Could it be that any of the changes we made i.e. renaming etc required a restart?
Finally, could anyone recommend a website that tells me what the full names of libraries are?


say i am looking for -lCint , but it is called something else in synaptic. 

The only packages that come up in synaptic when i search for cint are 
root-system-bin 
root-system

both are installed.Try ```
sudo apt-get install libroot-dev
```
which should put everything you need in /usr/lib/root. 

H

---

