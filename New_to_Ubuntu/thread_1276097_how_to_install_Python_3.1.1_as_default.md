---
title: "how to install Python 3.1.1 as default ?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by dave WB3DWE on 2009-09-26
[SIZE=3][FONT=Lucida Sans Unicode]There are threads re Python 2 weeks ago ( 6 posts, mostly 
brief )[/FONT][/SIZE] [FONT=Lucida Sans Unicode][SIZE=3]and in June. The latter suggests Synaptic Package Manager. The latest in the latter is 3.0.1 .  Python website strongly recommends 3.1 .
I've downloaded the 3.1.1 tar ball and extracted it.  README says       ./configure
              make
              make test
              sudo make install
"you must decide which version is your 'primary' version. Install that version using 'make install'.  Install all other versions using 'make altinstall' ".
Currently entering  python in the terminal brings up 2.6 .  I
want my primary version to be 3.1.1   Apparently this installation will overwrite 2.6 .  Is 2.6 used by Ubuntu or other apps and will overwriting this crash the system ?   Any other suggestions/help-       Thanks
[/SIZE][/FONT]

---

### Post by pedro3005 on 2009-09-26
[This guy]("http://ubuntuforums.org/showpost.php?p=7930414&postcount=3") seems to have compiled it and says it's running good, although I can't guarantee you that.

---

### Post by unutbu on 2009-09-26
Some system applications which use python will break if run under python3.

There are also many python modules (like pygame and numpy/scipy) which have not yet been ported to python3. Because of all these problems, python2.x is still the default "main" python used by Ubuntu.

---

### Post by dave WB3DWE on 2009-09-26
I don't know what this guy in Bangalore means by "compile it".  As far as I know a tarball is extracted and then installed.  I don't see what compiling has to do with installing an interpreted language.

---

### Post by btmiller on 2009-09-26
If you downloaded the source tarball, the program needs to be compiled (this is what the "make" step in your original post does). Python is mostly written in C IIRC.

I agree that you should leave the system's installed Python as the primary install and do the altinstall for 3.1.1. A number of system functions rely on Python and changing the version will break them as unutbu mentions.

---

