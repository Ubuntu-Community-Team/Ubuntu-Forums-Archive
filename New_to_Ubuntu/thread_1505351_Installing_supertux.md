---
title: "Installing supertux"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-09
I get an error while compiling supertux,and this is the error

```
karthick@Ubuntu-desktop:~/Desktop/supertux-0.3.3/buil$ cmake ..
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
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
CMake Error at /usr/share/cmake-2.8/Modules/FindBoost.cmake:894 (message):
  Unable to find the requested Boost libraries.

  Unable to find the Boost header files.  Please set BOOST_ROOT to the root
  directory containing Boost or BOOST_INCLUDEDIR to the directory containing
  Boost's headers.
Call Stack (most recent call first):
  CMakeLists.txt:65 (FIND_PACKAGE)


-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
CMake Error at mk/cmake/FindOggVorbis.cmake:48 (message):
  Could NOT find OggVorbis libraries
Call Stack (most recent call first):
  CMakeLists.txt:93 (FIND_PACKAGE)


CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
Boost_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/karthick/Desktop/supertux-0.3.3
OPENAL_INCLUDE_DIR
   used as include directory in directory /home/karthick/Desktop/supertux-0.3.3
SDLIMAGE_INCLUDE_DIR
   used as include directory in directory /home/karthick/Desktop/supertux-0.3.3
SDL_INCLUDE_DIR
   used as include directory in directory /home/karthick/Desktop/supertux-0.3.3

-- Configuring incomplete, errors occurred!

```

Can anyone give me a solution..?

---

### Post by bumanie on 2010-06-09
Why not install via synaptic or apt-get? 3.3-2 is in the repositories. Also have you got build-essential installed? This gives you all the packages that are essential for building .deb packages from source. If you don't have that > sudo apt-get install build-essential

---

### Post by karthick87 on 2010-06-09
> **bumanie said:**
> Why not install via synaptic or apt-get? 3.3-2 is in the repositories. Also have you got build-essential installed? This gives you all the packages that are essential for building .deb packages from source. If you don't have that


I have already installed build-essential package

---

