---
title: "Advanced Options for NVIDIA Installer program"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by newport_j on 2009-04-29
--x-library-path=X-LIBRARY-PATH
      The path under which the NVIDIA X libraries will be
      installed.  If this option is not specified,
      nvidia-installer uses the following search order and
      selects the first valid directory it finds: 1) `X
      -showDefaultLibPath`, 2) `pkg-config --variable=libdir
      xorg-server`, or 3) the X prefix (see the '--x-prefix'
      option) plus 'lib' on 32bit systems, and either 'lib64' or
      'lib' on 64bit systems, depending on the installed Linux
      distribution.

  

  --opengl-libdir=OPENGL-LIBDIR
      The path relative to the OpenGL library installation prefix
      under which the NVIDIA OpenGL components will be installed.
      The default is 'lib' on 32bit systems, and 'lib64' or 'lib'
      on 64bit systems, depending on the installed Linux
      distribution.  Only under very rare circumstances should
      this option be used.

The two above are advanced options used in the NVIDIA installer for NVIDIA drivers. 
I am unsure of the syntax to use on them. I am showing the general explanation of them when one uses the --advanced-options when running the NVIDIA installer. I want to declare different paths for them because as I said in a previous post, I do not want to interfere with existing NVIDIA drivers either X library or openGL.These new files are to be installed only for parallel processing. They must not interfere with the existing already installed NVIDIA graphics drivers so I must declare different path for them for this reason.


Now when I run this option and capture the screen, I get the following.


james ~/Desktop$ sudo ./NVIDIA-Linux-x86-180.22-pkg1.run --info --x-library-path='X -showDefaultLibPath'

  Identification    : NVIDIA Accelerated Graphics Driver for Linux-x86 180.22
  Target directory  : NVIDIA-Linux-x86-180.22-pkg1
  Uncompressed size : 59268 KB
  Compression       : gzip
  Date of packaging : Tue Jan  6 10:30:59 PST 2009
  Application run after extraction : ./nvidia-installer 

  The directory NVIDIA-Linux-x86-180.22-pkg1 will be removed after extraction. 


It does not say anything about the  'X --showDefaultLibPath'. I thought if I could see a default path I might have an idea of the new paths. It was not to be.

What is the syntax for these two options shown at the beginning of this post?

Newport_j

---

