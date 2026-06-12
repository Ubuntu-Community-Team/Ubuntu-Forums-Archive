---
title: "ktorrent 4.1 installing"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by mafi127 on 2011-03-24
the new ktorrent is out for some time now, but it still not in the package manager :(. Can some1 tel me how can I install the new version of ktorrent? I have downloaded the tar faile from the website, but I dont know how can I install it to my pc :(

---

### Post by mastablasta on 2011-03-24
tar file will have instructions. You can extract it to a folder and then find the instructions file  (e.g readme.txt, install.txtx...) on how to install it.

---

### Post by andrewthomas on 2011-03-24
Make sure that you use checkinstall to make a .deb and not make install.  

This way your package manager will be able to track the package.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by oldos2er on 2011-03-24
[http://ktorrent.org/wiki/index.php/FAQ#How_do_I_compile_KTorrent.3F](http://ktorrent.org/wiki/index.php/FAQ#How_do_I_compile_KTorrent.3F)

---

### Post by oklokl on 2011-03-24
qbittorrent
Recommended
New program :D

synaptic install
easy install

---

### Post by mafi127 on 2011-03-24
Thank you for replay guiz. I got problem when I compile libktorrent. When I make 

cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..

I got this error:
[PHP]tamps@tamps:~/Downloads/libktorrent-1.1.0/build$ cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.7.0 (using /usr/bin/qmake)
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Found X11: /usr/lib/libX11.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE 
-- Looking for _POSIX_TIMERS
-- Looking for _POSIX_TIMERS - found
-- Found Automoc4: /usr/bin/automoc4 
-- Found Perl: /usr/bin/perl 
-- Found Phonon: /usr/include  (found version "4.4.2", required is "4.3.80")
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.5 include dir: /usr/include
-- Found KDE 4.5 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Found GMP: /usr/include 
-- Boost version: 1.42.0
-- Found QCA2: /usr/lib/libqca.so 
-- Could not find libgcrypt includes.
-- Could not find libgcrypt library.
-- Looking for include files HAVE_XFS_XFS_H
-- Looking for include files HAVE_XFS_XFS_H - not found.
-- Looking for fopen64
-- Looking for fopen64 - found
-- Looking for fseeko64
-- Looking for fseeko64 - found
-- Looking for fseeko
-- Looking for fseeko - found
-- Looking for ftello64
-- Looking for ftello64 - found
-- Looking for ftello
-- Looking for ftello - found
-- Looking for fstat64
-- Looking for fstat64 - found
-- Looking for stat64
-- Looking for stat64 - found
-- Looking for ftruncate64
-- Looking for ftruncate64 - found
-- Looking for lseek64
-- Looking for lseek64 - found
-- Looking for mmap64
-- Looking for mmap64 - found
-- Looking for munmap64
-- Looking for munmap64 - not found
-- Looking for posix_fallocate64
-- Looking for posix_fallocate64 - found
-- Looking for posix_fallocate
-- Looking for posix_fallocate - found
-- Looking for fallocate
-- Looking for fallocate - found
-- Looking for statvfs
-- Looking for statvfs - found
-- Looking for statvfs64
-- Looking for statvfs64 - found
-- Could NOT find Doxygen  (missing:  DOXYGEN_EXECUTABLE) 
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
LIBGCRYPT_INCLUDE_DIR
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/torrent
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/torrent/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/datachecker
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/datachecker/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/download
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/download/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/diskio
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/diskio/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/peer
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/peer/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/net
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/net/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/mse
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/mse/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/magnet
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/magnet/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/util
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/util/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/utp
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/utp/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/upnp
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/tracker
LIBGCRYPT_LIBRARIES
    linked by target "ktorrent" in directory /home/tamps/Downloads/libktorrent-1.1.0/src

-- Configuring incomplete, errors occurred!
tamps@tamps:~/Downloads/libktorrent-1.1.0/build$ make
make: *** No targets specified and no makefile found.  Stop.
[/PHP]
how can I fix it :confused:

---

### Post by andrewthomas on 2011-03-24
You probably need to edit the CMakeCache.txt file.  

You should be able to right click on the file and choose "Open With CMake" and uncheck any options that do not apply to you.
[COLOR=#000000][COLOR=#007700]
[/COLOR][COLOR=#0000bb]Looking [/COLOR][COLOR=#007700]for [/COLOR][COLOR=#0000bb]Q_WS_WIN [/COLOR][COLOR=#007700]- [/COLOR][COLOR=#0000bb]not found[/COLOR][COLOR=#007700].[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000bb]Looking [/COLOR][COLOR=#007700]for [/COLOR][COLOR=#0000bb]Q_WS_QWS [/COLOR][COLOR=#007700]- [/COLOR][COLOR=#0000bb]not found[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]
[/COLOR][COLOR=#0000bb]Looking [/COLOR][COLOR=#007700]for [/COLOR][COLOR=#0000bb]Q_WS_MAC [/COLOR][COLOR=#007700]- [/COLOR][COLOR=#0000bb]not found[/COLOR][COLOR=#007700].

Also try and decline to build the documentation.
[/COLOR][/COLOR]

---

### Post by rikhar on 2011-03-25
> **mafi127 said:**
> Thank you for replay guiz. I got problem when I compile libktorrent. When I make 

cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..

I got this error:
[PHP]tamps@tamps:~/Downloads/libktorrent-1.1.0/build$ cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.7.0 (using /usr/bin/qmake)
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Found X11: /usr/lib/libX11.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE 
-- Looking for _POSIX_TIMERS
-- Looking for _POSIX_TIMERS - found
-- Found Automoc4: /usr/bin/automoc4 
-- Found Perl: /usr/bin/perl 
-- Found Phonon: /usr/include  (found version "4.4.2", required is "4.3.80")
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Found KDE 4.5 include dir: /usr/include
-- Found KDE 4.5 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Found GMP: /usr/include 
-- Boost version: 1.42.0
-- Found QCA2: /usr/lib/libqca.so 
-- Could not find libgcrypt includes.
-- Could not find libgcrypt library.
-- Looking for include files HAVE_XFS_XFS_H
-- Looking for include files HAVE_XFS_XFS_H - not found.
-- Looking for fopen64
-- Looking for fopen64 - found
-- Looking for fseeko64
-- Looking for fseeko64 - found
-- Looking for fseeko
-- Looking for fseeko - found
-- Looking for ftello64
-- Looking for ftello64 - found
-- Looking for ftello
-- Looking for ftello - found
-- Looking for fstat64
-- Looking for fstat64 - found
-- Looking for stat64
-- Looking for stat64 - found
-- Looking for ftruncate64
-- Looking for ftruncate64 - found
-- Looking for lseek64
-- Looking for lseek64 - found
-- Looking for mmap64
-- Looking for mmap64 - found
-- Looking for munmap64
-- Looking for munmap64 - not found
-- Looking for posix_fallocate64
-- Looking for posix_fallocate64 - found
-- Looking for posix_fallocate
-- Looking for posix_fallocate - found
-- Looking for fallocate
-- Looking for fallocate - found
-- Looking for statvfs
-- Looking for statvfs - found
-- Looking for statvfs64
-- Looking for statvfs64 - found
-- Could NOT find Doxygen  (missing:  DOXYGEN_EXECUTABLE) 
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
LIBGCRYPT_INCLUDE_DIR
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/torrent
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/torrent/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/datachecker
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/datachecker/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/download
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/download/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/diskio
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/diskio/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/peer
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/peer/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/net
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/net/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/mse
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/mse/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/magnet
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/magnet/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/util
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/util/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/utp
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/utp/tests
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/upnp
   used as include directory in directory /home/tamps/Downloads/libktorrent-1.1.0/src/tracker
LIBGCRYPT_LIBRARIES
    linked by target "ktorrent" in directory /home/tamps/Downloads/libktorrent-1.1.0/src

-- Configuring incomplete, errors occurred!
tamps@tamps:~/Downloads/libktorrent-1.1.0/build$ make
make: *** No targets specified and no makefile found.  Stop.
[/PHP]
how can I fix it :confused:
You should install libgcrypt11-dev package.

---

### Post by mafi127 on 2011-03-28
Thank you, got libktorrent installed now. Now I have another problem when I try to install ktorrent. when I type make then I got somekindow error and it will be terminated.

[PHP]tamps@tamps:~/Downloads/ktorrent-4.1.0/build$ make
Scanning dependencies of target ktcore_automoc
Generating chunkbar.moc
Generating prefpageinterface.moc
Generating plugin.moc
Generating torrentfilelistmodel.moc
Generating coreinterface.moc
Generating queuemanager.moc
Generating torrentfilemodel.moc
Generating torrentfiletreemodel.moc
Generating moc_centralwidget.cpp
Generating moc_activity.cpp
Generating moc_jobprogresswidget.cpp
Generating moc_dbus.cpp
Generating moc_dbussettings.cpp
Generating moc_extender.cpp
Generating moc_dbustorrent.cpp
Generating moc_tabbarwidget.cpp
Generating moc_stringcompletionmodel.cpp
Generating moc_hintlineedit.cpp
Generating moc_dbustorrentfilestream.cpp
Generating moc_pluginactivity.cpp
Generating moc_itemselectionmodel.cpp
Generating moc_groupmanager.cpp
Generating moc_jobtracker.cpp
Generating moc_dbusgroup.cpp
Generating moc_basicjobprogresswidget.cpp
[  0%] Built target ktcore_automoc
[  0%] Generating settings.h, settings.cpp
[  1%] Generating ui_basicjobprogresswidget.h
Scanning dependencies of target ktcore
[  2%] Building CXX object libktcore/CMakeFiles/ktcore.dir/ktcore_automoc.o
In file included from /home/tamps/Downloads/ktorrent-4.1.0/build/libktcore/moc_dbustorrentfilestream.cpp:10,
                 from /home/tamps/Downloads/ktorrent-4.1.0/build/libktcore/ktcore_automoc.cpp:14:
/home/tamps/Downloads/ktorrent-4.1.0/build/libktcore/../../libktcore/dbus/dbustorrentfilestream.h:26: fatal error: torrent/torrentfilestream.h: No such file or directory
compilation terminated.
make[2]: *** [libktcore/CMakeFiles/ktcore.dir/ktcore_automoc.o] Error 1
make[1]: *** [libktcore/CMakeFiles/ktcore.dir/all] Error 2
make: *** [all] Error 2
tamps@tamps:~/Downloads/ktorrent-4.1.0/build$ 
[/PHP]

What package I dont have now installed? :confused:

---

### Post by SeijiSensei on 2011-03-28
Try running "sudo apt-get build-dep ktorrent" and try again.  This handy command will download any source dependencies the target package requires.

---

### Post by mafi127 on 2011-03-28
Yeah, I did that before I did "cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix)" command

I get this message when I do apt cmd
[PHP]sudo apt-get build-dep ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/PHP]

---

### Post by Redwol on 2011-06-26
I have the same issue, if anyone has resolved this please post it here.

---

