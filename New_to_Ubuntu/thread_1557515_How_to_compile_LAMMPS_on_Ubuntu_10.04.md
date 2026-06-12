---
title: "How to compile LAMMPS on Ubuntu 10.04"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by lan1967 on 2010-08-20
Hello, everyone!
I wish I knew how to get bin file from the source for LAMMPS.
I used makefile.ubuntu prepared for Ubuntu 9.10 but probably it doesn't work.
Here is the original of the post:
[http://ubuntuforums.org/showthread.php?t=1390490](http://ubuntuforums.org/showthread.php?t=1390490)
Thank you for your attention.
Here is what I got in my terminal.
belial@belial-laptop:~/mylammps/src:~/mylammps/src$ make ubuntu
make[1]: Entering directory `/home/belial/mylammps/src/Obj_ubuntu'
g++ -O -DFFT_FFTW -DLAMMPS_GZIP -I../STUBS -c fix_poems.cpp
fix_poems.cpp:25:23: error: workspace.h: No such file or directory
fix_poems.cpp: In constructor &#8216;LAMMPS_NS::FixPOEMS::FixPOEMS(LAMMPS_NS::LAMMPS*, int, char**)&#8217;:
fix_poems.cpp:244: error: invalid use of incomplete type &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.h:95: error: forward declaration of &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.cpp: In destructor &#8216;virtual LAMMPS_NS::FixPOEMS::~FixPOEMS()&#8217;:
fix_poems.cpp:305: warning: possible problem detected in invocation of delete operator:
fix_poems.cpp:305: warning: invalid use of incomplete type &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.h:95: warning: forward declaration of &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.cpp:305: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
fix_poems.cpp: In member function &#8216;virtual void LAMMPS_NS::FixPOEMS::setup(int)&#8217;:
fix_poems.cpp:676: error: invalid use of incomplete type &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.h:95: error: forward declaration of &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.cpp: In member function &#8216;virtual void LAMMPS_NS::FixPOEMS::initial_integrate(int)&#8217;:
fix_poems.cpp:691: error: invalid use of incomplete type &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.h:95: error: forward declaration of &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.cpp: In member function &#8216;virtual void LAMMPS_NS::FixPOEMS::final_integrate()&#8217;:
fix_poems.cpp:768: error: invalid use of incomplete type &#8216;struct LAMMPS_NS::Workspace&#8217;
fix_poems.h:95: error: forward declaration of &#8216;struct LAMMPS_NS::Workspace&#8217;
make[1]: *** [fix_poems.o] Error 1
make[1]: Leaving directory `/home/belial/mylammps/src/Obj_ubuntu'
make: *** [ubuntu] Error 2

---

### Post by tyler.harvey3 on 2010-09-28
Were you trying to install it with parallel capability? 
I got serial installed just now on 10.04 fine, although I had to do
```
$ make -f Makefile.list ubuntu 
```
because
```
$ make ubuntu 
```
was having trouble dealing with wildcards. Haven't given parallel a shot yet.

---

