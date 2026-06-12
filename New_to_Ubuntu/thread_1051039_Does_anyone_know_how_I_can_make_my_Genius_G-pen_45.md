---
title: "Does anyone know how I can make my Genius G-pen 450 tablet work on Ubuntu 8.04?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-01-26
Does anyone know how I can make my Genius G-pen 450 tablet work on Ubuntu 8.04?

---

### Post by NewJack on 2009-01-26
Maybe it will work using the Wacom drivers.  Try this link for additional help:

[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

I don't use one myself, just thought this may help.  Good Luck!!!

---

### Post by NewJack on 2009-01-26
Actually, after posting the above link, I ended up finding this:

[https://www.not404.com/content/howtouse-genius-mousepen-8x6-tablet-fedora-9](https://www.not404.com/content/howtouse-genius-mousepen-8x6-tablet-fedora-9)

Comment #3 states that this How-To works with your tablet.  

Good Luck

P.S.- Make sure to post your results if this works.  There may be others with the same tablet as you that can use the help.

---

### Post by ivanvajar on 2009-01-27
Thank you for replying. I did what the manual says, but, when I run

 ./configure --with-xorg-modules-dir=/usr/lib/xorg/modules/input/

I get the message:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

How do I fix that?

---

### Post by ivanvajar on 2009-02-01
This thing works!

---

### Post by russu52 on 2009-02-01
that's good news! i have a nisis graphics tablet and had the same experience. at first it seemed to be dead, and then it worked perfectly. 

good luck

---

### Post by ximarix on 2009-02-19
Hey everybody,

when I try to run ./configure it hangs on the following error:

simon@simon-laptop:~/Desktop/wizardpen-0.6.0.2$ ./configure --with-xorg-modules-dir=/usr/lib/xorg/modules/input/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
[.........]
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto ) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I have installed xserver-xorg-dev and some xproto11-*-dev packages, but the message on configure is the same..

Any solutions? Is this because the package is called xserver-xorg on Ubuntu and xorg--x11-xserver on Fedora?

ivanvajar: What packages did you install?

---

