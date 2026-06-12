---
title: "installation error: Dependency is not satisfiable"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by flylehe on 2009-11-03
Hi,

On my Ubuntu 8.10, I tried to install a library libucil2 by double clicking its deb file libucil2-dev_0.9.5-1build2_i386.deb, but got "Error: Dependency is not satisfiable: llbucil2" like error. Any idea what is happening?

Thanks and regards!

---

### Post by phidia on 2009-11-03
Apt determines when there is a conflict or un-installable dependent package and you get a message like this.
Could you provide more info on what you are trying to do plus whether you are using 32 or 64 bit 8.10?

---

### Post by flylehe on 2009-11-03
Thanks, phidia!

Sorry a little late for getting back to you. My Ubuntu is 32 bit, so I use i386 instead of amd64 version of the library. 

I am trying to build OpenCV 2.0 from its source code via CMake following the installation guide of Opencv website ([http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)), but I got errors like:

> 
tim@tim:~/program_files/tim/OpenCV-2.0.0/release$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..
-- Detected version of GNU GCC: 43
-- checking for module 'libunicap'
--   package 'libunicap' not found
-- checking for module 'libucil'
--   package 'libucil' not found
-- checking for module 'libv4l1'
--   package 'libv4l1' not found
-- Could NOT find Jasper
-- IPP detected: 
-- Parsing 'cvconfig.h.cmake'
running mkdir -p "/home/tim/program_files/tim/OpenCV-2.0.0/release/unix-install/"  2>&1
-- 
-- General configuration for opencv 2.0.0 =====================================
-- 
--     Compiler:                  
--     C++ flags (Release):         -Wall -pthread -ffunction-sections  -O3 -DNDEBUG  -fomit-frame-pointer -O3 -ffast-math -mmmx -DNDEBUG 
--     C++ flags (Debug):           -Wall -pthread -ffunction-sections  -g  -O0 -DDEBUG -D_DEBUG 
--     Linker flags (Release):     
--     Linker flags (Debug):       
-- 
--   GUI: 
--     GTK+ 2.x:                  1
--     GThread:                   1
-- 
--   Image I/O: 
--     JPEG:                      TRUE
--     PNG:                       TRUE
--     TIFF:                      TRUE
--     JASPER:                    FALSE
-- 
--   Video I/O: 
--     DC1394 1.x:                
--     DC1394 2.x:                1
--     FFMPEG:                    1
--       codec:                   1
--       format:                  1
--       util:                    1
--       swscale:                 1
--       gentoo-style:            1
--     GStreamer:                 1
--     UniCap:                    
--     V4L/V4L2:                  1/1
--     Xine:                      1
-- 
--   Interfaces: 
--     Old Python:                0
--     Python:                    ON
--     Use IPP:                   NO
--     Build Documentation        0
-- 
--     Install path:              /usr/local
-- 
--     cvconfig.h is in:          /home/tim/program_files/tim/OpenCV-2.0.0/release
-- -----------------------------------------------------------------
-- 
-- Configuring done
-- Generatim done
-- Build files have been written to: /home/tim/program_files/tim/OpenCV-2.0.0/release



I thought I had to install the libraries it said as not found. So I looked for the libraries in Synaptic Package Manager but found nothing. I also tried to search them on Ubuntu website and found some related deb packages, like libucil2-dev and libunicap2-dev, but got a new error saying "dependencies not satiable" when trying to install them .

Any hint or advice? 

Thanks and regards!

---

