---
title: "Linksys WUSB54GSC USB Wireless ?"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by cville on 2006-08-02
On my Dapper Drake 6.06 LTS dont work also after I install the windows drivers, if I put on a windows pc work very well ?
Any suggestions ?

Thanks

---

### Post by amp_man on 2006-08-02
[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588) did you read this?

---

### Post by cville on 2006-08-02
Its related to WUSB54G and NOT WUSB54GSC..
I did all the test but nothing successfull.. :(

---

### Post by cville on 2006-08-04
*** Bumps ***

---

### Post by quickgun on 2006-09-24
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Follow Method 1 for the wusb54gsv2.

Upgrade ndiswrapper from source to vers. 1.8(Available at their sourceforge website)

modprobe ndiswrapper and voila, should work after you installed it properly.

---

### Post by knichel on 2006-09-25
I am trying to install this so I can use my WUSB54GSC USB network adapter.  I tried to download and install the ndiswrapper from sourceforge.net and when I follow the instructions, I get the following errors... If anybody can assist a newbie I would appreciate it.  

--
Mike

> knichel@knichel:~/Desktop/ndiswrapper-1.23$ make uninstall
NOTE: Not all installed files are removed, as different distributions install nd iswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear bel ow.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1

knichel@knichel:~/Desktop/ndiswrapper-1.23$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install nd iswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear bel ow.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /usr/sbin/ndiswrapper-buginfo
removing /lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrappe r': Is a directory
make: *** [uninstall] Error 1

knichel@knichel:~/Desktop/ndiswrapper-1.23$ sudo make
make -C driver
make[1]: Entering directory `/home/knichel/Desktop/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/knichel/Desktop/ndiswrapper-1.23/driver'
make: *** [all] Error 2
knichel@knichel:~/Desktop/ndiswrapper-1.23$ sudo make insatll
make: *** No rule to make target `insatll'.  Stop.

knichel@knichel:~/Desktop/ndiswrapper-1.23$ sudo make install
make -C driver install
make[1]: Entering directory `/home/knichel/Desktop/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/knichel/Desktop/ndiswrapper-1.23/driver'
make: *** [install] Error 2
knichel@knichel:~/Desktop/ndiswrapper-1.23$

---

### Post by quickgun on 2006-09-25
You must first remove the Ubuntu version of the ndiswrapper-utils package:
sudo apt-get remove ndiswrapper-utils

Then you must 'sudo apt-get install' whatever kernel headers version you're running.
sudo apt-get install kernel-headers-`uname -r`

Then in the ndiswrapper source directory which you decompressed and untarred, execute: 
sudo make and sudo make install
Finally, you must cd into the utils directory and execute:
sudo make install

Then check the versions with: 
ndiswrapper -v

After that, follow Method 1 from the above link.
In fact, you could liberally follow another howto posted on this forum concerning the WUSB54GSv2.  I only just got this device working last night after much work.

---

### Post by whatever123 on 2006-10-14
I was unable to get the bcrmndis.inf to install.  Error was:

<blockquote>
couldn't create /etc/ndiswrapper/bcmrndis: Permission denied at /usr/sbin/ndiswrapper line 138
</blockquote>

I've also been unable to uninstall the original .inf file on the CD.  Please help!

---

### Post by mo_x on 2006-10-24
You could try building a newer version of the driver.
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

---

