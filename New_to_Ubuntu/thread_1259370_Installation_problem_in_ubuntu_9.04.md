---
title: "Installation problem in ubuntu 9.04"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by sourabhg on 2009-09-06
I  downloaded i915graphics.tar.gz.
I do not how to install the file
It does not even contain .deb files

---

### Post by lswb on 2009-09-06
If you are trying to correct intel graphics problems this thread
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1130582](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1130582)
has good instructions and links to deb packages that will make it relatively easy. The .tar.gz package you downloaded is likely a source code package that needs to be compiled and manually installed.

---

### Post by Claus7 on 2009-09-06
Hello,

in order to install such a file most of the time after you unzip it, you have to do the "hard way": meaning that you have to install it yourself.

There it should have README files and/or INSTALLATION files and/or CONFIGURE (configure) files. First take a look at them and see what they talking about in order to help you for the installation.

Most of the time in these circumstances, what you have to do is:
i)untar or unzip the file
ii)enter to the untared folder and type:
./configure
make
make install (or sudo make install if you have permission problems).

If you are lucky, the program you just downloaded will be installed pretty smoothly.

Try these things out and let us know.

Regards!

---

### Post by mapes12 on 2009-09-06
Hopefully you have your problem sorted. This may be helpful for the future: 

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

and welcome to the Ubu community.

---

### Post by 3rdalbum on 2009-09-06
> **sourabhg said:**
> I  downloaded i915graphics.tar.gz.
I do not how to install the file
It does not even contain .deb files

Welcome to Ubuntu.

Ubuntu already contains a graphics card driver for the Intel 915 graphics chipset, and it is used by default if you have one of these graphics chips. In fact, Ubuntu contains a LOT of drivers for various things, which will be used if the appropriate hardware is present.

This is a lot different to Windows, and it's one of the things that people really appreciate about Linux.

I hope you enjoy using Ubuntu, and if you have any other problems please feel free to ask, as long as you give us as much information about your problem as possible.

Chris.

---

