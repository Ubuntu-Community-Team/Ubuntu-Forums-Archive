---
title: "Install issue with RT2570"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by sotherls on 2007-10-04
This is an operator error issue I know but I have followed all (well most of them) of the posts related to this issue.

I have downloaded the latest drivers for this from serialmonkey and performed the steps to move it into the /usr/src directory. When I cd to the Module directory and I run the 'sudo make' command I get the following:

scott@ubuntu:/usr/src/rt2570-1.1.0-b2/Module$ sudo make
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
/bin/sh: gcc-3.4: command not found
make[2]: *** [/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o] Error 127
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b2/Module] Error 2
make: *** [module] Error 1
scott@ubuntu:/usr/src/rt2570-1.1.0-b2/Module$

As you can guess I am new to Ubuntu and Linux - trying to come over to the light!

Any help would be appreciated!

---

### Post by Lambert on 2007-10-05
> **sotherls said:**
> This is an operator error issue I know but I have followed all (well most of them) of the posts related to this issue.

I have downloaded the latest drivers for this from serialmonkey and performed the steps to move it into the /usr/src directory. When I cd to the Module directory and I run the 'sudo make' command I get the following:

scott@ubuntu:/usr/src/rt2570-1.1.0-b2/Module$ sudo make
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
/bin/sh: gcc-3.4: command not found
make[2]: *** [/usr/src/rt2570-1.1.0-b2/Module/rtusb_main.o] Error 127
make[1]: *** [_module_/usr/src/rt2570-1.1.0-b2/Module] Error 2
make: *** [module] Error 1
scott@ubuntu:/usr/src/rt2570-1.1.0-b2/Module$

As you can guess I am new to Ubuntu and Linux - trying to come over to the light!

Any help would be appreciated!

Ubuntu does not come with the packages to build apps. You need to install a package called build-essential (I believe that's correct). Also check the readme file of the drivers to see if there are any other packages that need to be installed.

To learn some more about basics, you can read some info at [http://doc.gwos.org/doku.php/doc:admin](http://doc.gwos.org/doku.php/doc:admin) and also wiki.ubuntu.com and help.ubuntu.com

---

