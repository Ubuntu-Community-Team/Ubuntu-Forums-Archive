---
title: "&quot;make&quot; error"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by noseshark on 2010-01-24
[FONT=Century Gothic][SIZE=2]I want to install Jahshaka but when I type make this happends[/SIZE][/FONT]

[FONT=Century Gothic][SIZE=2][COLOR=Red]make: *** No targets specified and no makefile found.  Stop.[/COLOR][/SIZE][/FONT]


[FONT=Century Gothic][SIZE=2]Everything looks like this:[/SIZE][/FONT]

[FONT=Century Gothic][SIZE=2][COLOR=Red]val@ubuntu:~$ cd ./Documents/Programs/jahshaka
val@ubuntu:~/Documents/Programs/jahshaka$ ./configure
>>Configuring build type for jahshaka

./configure: 57: qmake: not found
---------------------------------------
Jahshaka Configure Script User Commands
---------------------------------------

SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries

val@ubuntu:~/Documents/Programs/jahshaka$ make
make: *** No targets specified and no makefile found.  Stop.
val@ubuntu:~/Documents/Programs/jahshaka$ 
[COLOR=Black]
someone please help, how can I fix this?[/COLOR]
[/COLOR][/SIZE][/FONT]

---

### Post by baddog144 on 2010-01-24
It looks like you need `qmake`, which  you can get with 
```

sudo apt-get install qt4-qmake

```

---

### Post by noseshark on 2010-01-24
I installed qmake so now it lets me put in "make"
but, what do I do after make?
I tryed sudo checkinstall -D & make install
it doesn't seem to be working :/

---

### Post by baddog144 on 2010-01-24
What is the error you get?

---

### Post by noseshark on 2010-01-24
[COLOR=Red]val@ubuntu:~$ cd ./Documents/Programs/jahshaka
val@ubuntu:~/Documents/Programs/jahshaka$ ./configure
>>Configuring build type for jahshaka

Project MESSAGE: Jahshaka 2.0 build system
Project MESSAGE: -----------------------------
Project MESSAGE: 
Project MESSAGE: Checking operating system and paths
Project MESSAGE: 
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: 
Project MESSAGE: JAHPREFIX="/usr/local" _THREAD_SAFE=true JAHTHEMES JAHGIFT NVIDIA_GPU JAHSCRIPT JAHLINUX
Project MESSAGE: /usr/include/freetype2 /usr/local/include /usr/include
Project MESSAGE: 
Project MESSAGE: Building Jahshaka 2.0
Project MESSAGE: ---------------------
Project MESSAGE: 
Project MESSAGE: Configuring Subsystems
Project MESSAGE: ----------------------
Project MESSAGE: 
Project MESSAGE: >> Configuring Auxillary Libraries
Project MESSAGE: 
Project MESSAGE: >> Configuring OpenLibraries
Project MESSAGE: Configuring Jahshaka
Project MESSAGE: --------------------
Project MESSAGE: 
Project MESSAGE: Configuring JahCore
Project MESSAGE: Configuring JahDesktop
Project MESSAGE: Configuring JahLibraries
Project MESSAGE: Configuring JahModules
Project MESSAGE: Configuring JahSource
Project MESSAGE: Configuring JahWidgets
Project MESSAGE: Configuring Jahshaka Linker
Project MESSAGE: 
Project MESSAGE: Finished Configuring Subsystems
Project MESSAGE: -------------------------------
Project MESSAGE: 
Project MESSAGE: Configuring Plugin Support
Project MESSAGE:  
Project MESSAGE: Make files have been configured
Project MESSAGE: type make to build
Project MESSAGE: 
Project MESSAGE: please file all bugs at [http://bugs.jahshaka.org](http://bugs.jahshaka.org)
Project MESSAGE: 

SUMMARY

     Configuration complete.

     Building         = jahshaka
     Install prefix   = /usr/local
     Debug            = true
     Static libs      = false
     Building plugins = true
     OpenAL framework = false

BUILD AND INSTALL

     To build the application and plugins, run:

     $ make

     To install, run this as your superuser:

     # make install

val@ubuntu:~/Documents/Programs/jahshaka$ make
cd source/AuxiliaryLibraries/ && make -f Makefile 
make[1]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
/usr/bin/qmake -unix -o Makefile AuxiliaryLibraries.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring AuxilliaryLibraries
Project MESSAGE: -------------------------------
make[1]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
make[1]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
cd blur/ && make -f Makefile 
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
/usr/bin/qmake -unix -o Makefile blur.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && make -f Makefile 
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
/usr/bin/qmake -unix -o Makefile FTGL.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
g++ -c -pipe -g -w -fPIC -D_REENTRANT -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTBitmapGlyph.o FTBitmapGlyph.cpp
makIn file included from FTBitmapGlyph.cpp:3:
FTBitmapGlyph.h:5:22: error: ft2build.h: No such file or directory
FTBitmapGlyph.h:6:10: error: #include expects "FILENAME" or <FILENAME>
FTBitmapGlyph.h:7:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTBitmapGlyph.h:9,
                 from FTBitmapGlyph.cpp:3:
FTGL.h:44:31: error: GL/gl.h: No such file or directory
FTGL.h:45:32: error: GL/glu.h: No such file or directory
In file included from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTGlyph.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTGlyph.h:6:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTBBox.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTBBox.h:7:10: error: #include expects "FILENAME" or <FILENAME>
In file included from FTBBox.h:10,
                 from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTPoint.h:5:10: error: #include expects "FILENAME" or <FILENAME>
FTPoint.h:6:10: error: #include expects "FILENAME" or <FILENAME>
e In file included from FTBBox.h:10,
                 from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTPoint.h:39: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
FTPoint.h:39: error: ISO C++ forbids declaration of &#8216;FT_Vector&#8217; with no type
FTPoint.h: In constructor &#8216;FTPoint::FTPoint(int)&#8217;:
FTPoint.h:40: error: &#8216;ft_vector&#8217; was not declared in this scope
In file included from FTGlyph.h:8,
                 from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTBBox.h: At global scope:
FTBBox.h:49: error: expected `)' before &#8216;glyph&#8217;
In file included from FTBitmapGlyph.h:10,
                 from FTBitmapGlyph.cpp:3:
FTGlyph.h:31: error: expected `)' before &#8216;glyph&#8217;
FTGlyph.h:65: error: &#8216;FT_Error&#8217; does not name a type
FTGlyph.h:81: error: &#8216;FT_Error&#8217; does not name a type
In file included from FTBitmapGlyph.cpp:3:
FTBitmapGlyph.h:31: error: expected `)' before &#8216;glyph&#8217;
FTBitmapGlyph.cpp:5: error: expected `)' before &#8216;glyph&#8217;
make[2]: *** [FTBitmapGlyph.o] Error 1
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
make[1]: *** [sub-FTGL-make_default] Error 2
make[1]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries-make_default] Error 2
val@ubuntu:~/Documents/Programs/jahshaka$ make install
cd source/AuxiliaryLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
cd blur/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/particle'
/usr/bin/qmake -unix -o Makefile particle.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/apollon'
/usr/bin/qmake -unix -o Makefile apollon.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/apollon'
cd gift/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/gift'
/usr/bin/qmake -unix -o Makefile gift.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/gift'
cd spaceball/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/spaceball'
/usr/bin/qmake -unix -o Makefile spaceball.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/spaceball'
cd glew/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/glew'
/usr/bin/qmake -unix -o Makefile glew.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries/glew'
make[1]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/AuxiliaryLibraries'
cd source/OpenLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries'
/usr/bin/qmake -unix -o Makefile OpenLibraries.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring OpenLibraries
Project MESSAGE: -------------------------
make[1]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries'
make[1]: Entering directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries'
cd opencore/ && make -f Makefile install
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries/opencore'
/usr/bin/qmake -unix -o Makefile opencore.pro
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries/opencore'
make[2]: Entering directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries/opencore'
g++ -c -pipe -g -D_REENTRANT -Wall -W -fPIC -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.. -I../openimagelib -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o openpreferences.o openpreferences.cpp
openpreferences.cpp:10:20: error: qimage.h: No such file or directory
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:17:18: error: qmap.h: No such file or directory
../openimagelib/rgb.h:18:24: error: qptrvector.h: No such file or directory
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:32: error: expected template-name before &#8216;<&#8217; token
../openimagelib/rgb.h:32: error: expected `{' before &#8216;<&#8217; token
../openimagelib/rgb.h:32: error: expected unqualified-id before &#8216;<&#8217; token
make[2]: *** [openpreferences.o] Error 1
make[2]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries/opencore'
make[1]: *** [sub-opencore-install_subtargets] Error 2
make[1]: Leaving directory `/home/val/Documents/Programs/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries-install_subtargets] Error 2
val@ubuntu:~/Documents/Programs/jahshaka$ 

[/COLOR]

---

### Post by baddog144 on 2010-01-24
I think you'll also need libqt4-dev :P
and mesa-common-dev

---

