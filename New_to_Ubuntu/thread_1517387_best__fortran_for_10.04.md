---
title: "best_ fortran for 10.04"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Morpholinux on 2010-06-25
hi all!
(I did search this...but....)


how I know...if I have already a version of fortran in my computer (ubuntu 10.04) at the command line?

Which is the latest AND more stable version (in one word the best)(cause there are a bunch.. [https://help.ubuntu.com/community/InstallingCompilers)?](https://help.ubuntu.com/community/InstallingCompilers)?)

(this ...I think is the more...latest stuff when one googles it
[http://ubuntuforums.org/showthread.php?t=1082782](http://ubuntuforums.org/showthread.php?t=1082782))

that's right? 



I want/have to learn how to program in fortran....
and to compile...


thanks!

---

### Post by alphacrucis2 on 2010-06-25
> **Morpholinux said:**
> hi all!
(I did search this...but....)


how I know...if I have already a version of fortran in my computer (ubuntu 10.04) at the command line?

Which is the latest AND more stable version (in one word the best)(cause there are a bunch.. [https://help.ubuntu.com/community/InstallingCompilers)?](https://help.ubuntu.com/community/InstallingCompilers)?)

(this ...I think is the more...latest stuff when one googles it
[http://ubuntuforums.org/showthread.php?t=1082782](http://ubuntuforums.org/showthread.php?t=1082782))

that's right? 



I want/have to learn how to program in fortran....
and to compile...


thanks!

To install the gnu fortran compiler:

```
sudo apt-get install gfortran
```

---

### Post by Morpholinux on 2010-06-25
yup!
murpholinox@eva00:~$ gfortran --version
GNU Fortran (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2010 Free Software Foundation, Inc.

GNU Fortran comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of GNU Fortran
under the terms of the GNU General Public License.
For more information about these matters, see the file named COPYING

but...that does not explain...why its the best...

at least...its free that's a good point!

---

### Post by alphacrucis2 on 2010-06-25
> **Morpholinux said:**
> yup!
murpholinox@eva00:~$ gfortran --version
GNU Fortran (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2010 Free Software Foundation, Inc.

GNU Fortran comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of GNU Fortran
under the terms of the GNU General Public License.
For more information about these matters, see the file named COPYING

but...that does not explain...why its the best...

at least...its free that's a good point!

Have a look at the project web site and see if it meets your needs. Being associated with the gcc project probably gives it credibilty:

[http://gcc.gnu.org/]("http://gcc.gnu.org/")

I have a friend in another town who's job involves writing fortran software. Next time I get in contact with him I must ask what compiler he uses.

---

### Post by Morpholinux on 2010-06-26
okey dokey! 
Somebody told me...that 


"In general it doesn't matter which version you use
the gnu compilers (such as g77, gfortran) are a little bit more safe because they make a lot of checks at compile time
  with ifort is easier to make errors"


....
so...next question...
can I install three or four with no problems?


(maybe one tutorial uses one...another tutorial other etc etc)

---

