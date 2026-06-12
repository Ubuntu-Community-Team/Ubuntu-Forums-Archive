---
title: "Using the --advanced-options in NVIDIA installer"
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


It does not say anything about the 'X --showDefaultLibPath'. I thought if I could see a default path I might have an idea of the new paths. It was not to be.

What is the syntax for these two options shown at the beginning of this post?

Newport_j

---

### Post by Bachstelze on 2009-04-29
What makes you think you need to use those options in the first place?

---

### Post by newport_j on 2009-04-29
As I said, I cannot do a standard install of the NVIDA driver. I already have NVIDIA driver graphics installed. 

This installation is for parallel processing- a completely different thing from NVIDIA graphics. This uses the NVIDIA CUDA enabled graphics card and its software drivers are the same as that employed by a NVIDIA card, but that is where the simililarity ends.

The difference is:

1. this is a second installation of NVIDIA graphics

2. this is NVIDIA graphics card, and its drivers  must be installed, but for parallel processing of the GPU (in our case an NVIDIA graphics card). Hence, this card and its driver are independent of the originally installed drivers, thus they must be independently installed. I have taken care of the hardware, but I have had trouble installing the drivers - For Parallel Processing, not Graphics processing.


That is why I need to use the install options because this is an atypical use of the NVIDIA graphics card and its software.

Newport_j

---

