---
title: "Makefile wipes out folder"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by jon_herr on 2007-02-18
This is networking related only in the spirit of compiling drivers for the RTL 8180 from source.

I followed directions for compiling - basically running a makefile to compile the source using current kernel headers.  Well...

At the very beginning of executing makefile - all contents of source folder gets deleted.  Makefile continues but there are no files to compile...  

I can't see anything in the makefile that is deleting files?  I must be the overall make process?

Is this a bug?  

BTW:  I'm using Ubuntu - Edgy 6.10 with all current updates.  

I've compiled drivers from source in Dapper and not had this problem...


Jon

---

### Post by gradedcheese on 2007-02-18
can you post a link to the drivers?  I'd like to take a look at this Makefile and see if I can help sort this out.

---

### Post by jon_herr on 2007-02-18
Driver files:
[ftp://202.65.194.211/cn/wlan/rtl8180_linuxdrv_v15_fedora3.zip](ftp://202.65.194.211/cn/wlan/rtl8180_linuxdrv_v15_fedora3.zip)

Here's the behavior:

First I list the extracted folder contents:

<code>
jherr@vistabox:~/downloads/rtl8180_1.5_release26$ ls -l
total 1916
-rw-r--r-- 1 jherr jherr 1891989 2005-02-18 06:52 8180_26_private.ko
-rw-r--r-- 1 jherr jherr    1234 2005-01-20 16:37 Makefile
-rw-r--r-- 1 jherr jherr    4593 2005-01-20 16:37 r8180_if.h
-rw-r--r-- 1 jherr jherr   14010 2005-01-20 16:37 r8180_pci_init.c
-rw-r--r-- 1 jherr jherr     528 2005-01-20 16:37 r8180_pci_init.h
-rw-r--r-- 1 jherr jherr    9453 2005-01-20 16:37 r8180_type.h
-rw-r--r-- 1 jherr jherr    1039 2005-01-20 16:37 readme26.txt
-rw-r--r-- 1 jherr jherr     202 2005-01-20 16:37 rls_note_1220
-rwxrwxrwx 1 jherr jherr     188 2005-01-20 16:37 wlandown
-rwxrwxrwx 1 jherr jherr    4112 2005-02-18 07:59 wlanup
</code>
then I type "make all" which is the only option in the Makefile other than "make clean":

<code>
jherr@vistabox:~/downloads/rtl8180_1.5_release26$ make all
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/jherr/downloads/rtl8180_1.5_release26 MODVERDIR=/home/jherr/downloads/rtl8180_1.5_release26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
scripts/Makefile.build:17: /home/jherr/downloads/rtl8180_1.5_release26/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/jherr/downloads/rtl8180_1.5_release26/Makefile'.  Stop.
make[1]: *** [_module_/home/jherr/downloads/rtl8180_1.5_release26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [modules] Error 2
</code>

by the time the makefile gets to make[1] the folder contents are already gone:
<code>
make: *** [modules] Error 2
jherr@vistabox:~/downloads/rtl8180_1.5_release26$ ls
jherr@vistabox:~/downloads/rtl8180_1.5_release26$ 
</code>

---

### Post by christhemonkey on 2007-02-18
That link doesnt work for me?

Quick google led me here:
[http://sourceforge.net/project/downloading.php?group_id=114161&use_mirror=belnet&filename=rtl8180-0.21.tar.gz&81746479](http://sourceforge.net/project/downloading.php?group_id=114161&use_mirror=belnet&filename=rtl8180-0.21.tar.gz&81746479)

But i cant find a version 1.5 release 26 im afraid.... so i cant help.

EDIT: My firewall just seemed to have blocked it for some reason, it seems fine now.

---

### Post by gradedcheese on 2007-02-18
ah!  this is kind of interesting:  it's not deleting the files, it's moving them (check the output of the errors carefully), but having moved them the build fails and it stops there... with your files moved ;)

question: do you have your kernel headers installed?  If not, this build will of course failed:

1) run "uname -r" to see your kernel's name (ex: "2.6.17-10-386")
2) run "sudo apt-get install kernel-headers-put_the_name_here"
3) try 'make' again (you can just type "make", it does "make modules" by default anyway)

If you look at the Makefile, it's expecting /lib/modules/`uname -r` to exist.

---

### Post by jon_herr on 2007-02-18
Thanks for the response but I already have my kernel headers installed...  Everything but the "debug" headers.

My kernel is:  2.6.17-11-generic 

The path referred to by the script: 
/lib/modules/2.6.17-11-generic/build

exists and can be listed:

jherr@vistabox:~/downloads/rtl8180_1.5_release26$ ls /lib/modules/2.6.17-11-generic/build
arch  block  crypto  drivers  firmware  fs  include  init  ipc  kernel  lib  Makefile  mm  modules  Module.symvers  net  scripts  security  sound  usr

Although when I perform an ls -l on the folder I get a symbolic link:
lrwxrwxrwx 1 root root 40 2007-02-17 12:44 /lib/modules/2.6.17-11-generic/build -> /usr/src/linux-headers-2.6.17-11-generic

---

### Post by gradedcheese on 2007-02-18
oops, see next post

---

### Post by gradedcheese on 2007-02-18
do you have kernel source? (if not, install kernel-source and uncompress the archive in /usr/src/, it will be kernel-source-2.6.17.gz or something).  


Then you can just copy the driver's sources (ie: everything but the Makefile and readme) to:

/usr/src/linux-source-2.6.17/drivers/net/

and then:

cd /usr/src/linux-source-2.6.17
sudo make drivers/net/open8180.ko

Once done, look at their readme: they say to load one module and then the other in the right order.  They provided up/down scripts for this, so I guess you'll have to edit ifdown and ifup accordingly...

---

### Post by jon_herr on 2007-02-19
Thanks... will try tonight.

I think I have the source but can't say for certain...  If not then bad me.

Strange way for this problem to manifest itself!

---

### Post by eremini on 2007-03-17
have you ever gotten it to work?

---

