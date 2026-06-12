---
title: "Error during 'make'"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Dennis_Rocket on 2009-05-22
Hi guys,

I'm having troubles compiling a visualization freeware for linux, called daime. Hope someone can help me, here's the output for 'make':

g++ -c -pipe -O2 -O3 -fno-check-new -fexceptions -D_REENTRANT -w -DQT_NO_DEBUG -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I/usr/X11R6/include -I. -I. -o acoloc2dbase.o acoloc2dbase.cpp
acoloc2dbase.cpp: In member function ‘Mem::sptr<Proc::StackProcessor::Result> Proc::AColoc2DBase::ExecRandDipoles()’:
acoloc2dbase.cpp:523: error: ‘srand’ was not declared in this scope
acoloc2dbase.cpp:539: error: ‘rand’ was not declared in this scope
acoloc2dbase.cpp: In member function ‘Mem::sptr<Proc::StackProcessor::Result> Proc::AColoc2DBase::ExecRandDipolesMask()’:
acoloc2dbase.cpp:680: error: ‘srand’ was not declared in this scope
acoloc2dbase.cpp:697: error: ‘rand’ was not declared in this scope
make: *** [acoloc2dbase.o] Error 1

Thanks for any help!
Dennis

---

### Post by taseedorf on 2009-05-22
There are errors in the programming code.  The errors are because those functions (rand, srand) are not declared correctly in the source code.... if you know programming, you must declare them correctly...

---

