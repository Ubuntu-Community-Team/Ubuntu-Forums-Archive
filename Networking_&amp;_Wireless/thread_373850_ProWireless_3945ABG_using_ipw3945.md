---
title: "Pro/Wireless 3945ABG using ipw3945"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by CrazyTn on 2007-03-01
I am using this guide 
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Installed ieee80211-1.1.14 , but get the following error when I tried to install pw3945-1.1.3

Is the error from ieee80211?
"If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information."



```
First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from http://ieee80211.sf.net.  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.1.14.tgz
	% cd ieee80211-1.1.14
	% make 
	# make install   <--- You may need to be root
	% cd ..

If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information.

Once the ieee80211 subsystem is installed, we build the ipw3945.ko module:

	% tar xzvf ipw3945-1.1.3.tgz
	% cd ipw3945-1.1.3
	% make
```



```
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```

---

### Post by Len_C on 2007-03-01
If you are edgy user, try this before compiling:

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

---

### Post by CrazyTn on 2007-03-01
> **Len_C said:**
> If you are edgy user, try this before compiling:

sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

this would replace the shell command with bash?

---

### Post by CrazyTn on 2007-03-02
All I had to do was install the 

linux-restricted-modules-generic

works now

---

