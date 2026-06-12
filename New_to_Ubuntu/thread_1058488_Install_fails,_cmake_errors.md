---
title: "Install fails, cmake errors"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-02
I'm trying to install the yaWP widget, but I'm getting errors that another person has said he didn't get (original thread, "[_ISO a RELIABLE weather widget_](http://ubuntuforums.org/showthread.php?t=1057478)").  These are the same errors I got when I tried to manually compile the source code before.  On my previous quest to install a C++ compiler and whatever dependencies I thought I needed, I broke KDE to the point I could no longer login.  So step-by-step instructions might be needed! ^^;
```

gotaro@gotaro-linux:~/Downloads/yawp-0.1.65$ ./install.sh
KDE version: 4.2.00                                      
Using CMakeLists.kde42.txt                               
-- The C compiler identification is GNU                  
-- The CXX compiler identification is unknown            
-- Check for working C compiler: /usr/bin/gcc            
-- Check for working C compiler: /usr/bin/gcc -- works   
-- Detecting C compiler ABI info                         
-- Detecting C compiler ABI info - done                  
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.                  
-- Looking for Q_WS_X11                                                         
-- Looking for Q_WS_X11 - found                                                 
-- Looking for Q_WS_WIN                                                         
-- Looking for Q_WS_WIN - not found.                                            
-- Looking for Q_WS_QWS                                                         
-- Looking for Q_WS_QWS - not found.                                            
-- Looking for Q_WS_MAC                                                         
-- Looking for Q_WS_MAC - not found.                                            
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake)                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found                        
-- Looking for gethostbyname                                                    
-- Looking for gethostbyname - found                                            
-- Looking for connect                                                          
-- Looking for connect - found                                                  
-- Looking for remove                                                           
-- Looking for remove - found                                                   
-- Looking for shmat                                                            
-- Looking for shmat - found                                                    
-- Looking for IceConnectionNumber in ICE                                       
-- Looking for IceConnectionNumber in ICE - found                               
-- Found X11: /usr/lib/libX11.so                                                
-- Looking for include files CMAKE_HAVE_PTHREAD_H                               
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found                       
-- Looking for pthread_create in pthreads                                       
-- Looking for pthread_create in pthreads - not found                           
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
-- Performing Test _OFFT_IS_64BIT
CMake Error at /usr/share/cmake-2.6/Modules/CMakeCXXInformation.cmake:17 (GET_FILENAME_COMPONENT):
  get_filename_component called with incorrect number of arguments
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: CMAKE_CXX_COMPILER not set, after EnableLanguage
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Performing Test _OFFT_IS_64BIT - Failed
-- Phonon Version: 4.3.0
-- Found Phonon: /usr/lib/libphonon.so
-- Found Phonon Includes: /usr/include/KDE;/usr/include
-- Found KDE 4.2 include dir: /usr/include
-- Found KDE 4.2 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error at po/CMakeLists.txt:6 (MESSAGE):
  Please install the msgfmt binary


-- Configuring incomplete, errors occurred!
/home/gotaro/Downloads/yawp-0.1.65/build
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
Compilation failed, sorry :-(
```

---

### Post by Gotaro on 2009-02-03
Bump

---

