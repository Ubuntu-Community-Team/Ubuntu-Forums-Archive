---
title: "Modprobe ndiswrapper - not found???"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by bartt on 2008-05-07
Noob here.

I've been lurking here a while to learn about getting my laptop working on my wireless network. 
Finally took the plunge and installed the ndiswrapper common and util packages as outlined in other threads (thanks to KevDog), on my new Hardy install. 
Then I downloaded the Winbloz drivers from the realtek site and got as far as loading them with the ndiswrapper. So when I type ndiswrapper -l, I get back "net8187b : driver installed  device (0BDA:8197) present". So far so good. 
But when I try "sudo modprobe ndiswrapper", I get back "FATAL: Module ndiswrapper not found". 
This is stumping me. What do I need to do to fix this?
Thanks in advance.

---

### Post by Ayuthia on 2008-05-07
> **bartt said:**
> Noob here.

I've been lurking here a while to learn about getting my laptop working on my wireless network. 
Finally took the plunge and installed the ndiswrapper common and util packages as outlined in other threads (thanks to KevDog), on my new Hardy install. 
Then I downloaded the Winbloz drivers from the realtek site and got as far as loading them with the ndiswrapper. So when I type ndiswrapper -l, I get back "net8187b : driver installed  device (0BDA:8197) present". So far so good. 
But when I try "sudo modprobe ndiswrapper", I get back "FATAL: Module ndiswrapper not found". 
This is stumping me. What do I need to do to fix this?
Thanks in advance.
What does ndiswrapper -v say?

---

### Post by bartt on 2008-05-07
Hmm.. that's interesting.
ndiswrapper -v relies with several lines stating that "module version is too old!" and finally " You may need to upgrade driver and/or utils to latest versions avaiable at.. sourceforge"

I downloaded these files from ubuntu.com from the hardy section. I would think they are the latest ones or at least operational.

---

### Post by Ayuthia on 2008-05-07
You might want to make sure that you don't have any files with the name ndiswrapper in the directory when you run this check.  You might also try:
```
sudo updatedb
locate ndiswrapper.ko
```
updatedb will update the search database so that locate can see if the file that you are searching is there.

---

### Post by bartt on 2008-05-07
Thanks for your help..

I'm sorry you lost me- "any files with the name ndiswrapper in" which directory? 
As to the rest, I have to wait until I can reconnect this box to my wired network at home..

---

### Post by Ayuthia on 2008-05-07
Sometimes if there is a file called ndiswrapper in the directory when you type ndiswrapper -v, it can report a false version.  For example, in my /home/jayhawk directory, I have a file called ndiswrapper.  When I type ndiswrapper -v, I get:
```
jayhawk@allen-fieldhouse:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: Invalid argument
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: Invalid argument

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
```However, if I go to my Desktop where I have no files, I get:
```
jayhawk@allen-fieldhouse:~$ cd Desktop
jayhawk@allen-fieldhouse:~/Desktop$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload
```

EDIT:
By the way, the commands that I have requested do not require an internet connection.

EDIT 2: 
Unless you want to copy and paste back to the forum... :)

---

### Post by bartt on 2008-05-07
OK. I ran the requested commands and a couple of others for a sanity check:

bart@savantlaptop:~$ ls
Desktop    drivers   Music     Public     Videos
Documents  Examples  Pictures  Templates  wireless_stuff
bart@savantlaptop:~$ cd Desktop
bart@savantlaptop:~/Desktop$ ls
bart@savantlaptop:~/Desktop$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present
bart@savantlaptop:~/Desktop$ ndiswrapper -v
modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
bart@savantlaptop:~/Desktop$ 
bart@savantlaptop:~/Desktop$ 

bart@savantlaptop:~/Desktop$ locate ndiswrapper.ko
/home/bart/wireless_stuff/ndiswrapper-1.52/driver/.ndiswrapper.ko.cmd
/home/bart/wireless_stuff/ndiswrapper-1.52/driver/ndiswrapper.ko
bart@savantlaptop:~/Desktop$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
bart@savantlaptop:~/Desktop$ 

------------------------------------------------------------
looks to me like there are a couple of ndiswrapper files and the system is confused.
Do you think it is finding the file in my wireless_stuff dir ?
Since I did a package install shouldn't it find a file in a bin dir somewhere?

---

### Post by bartt on 2008-05-07
So it occured to me that i should download the latest from sourceforge. 
Did that and following the install file I have to build.. So assuming that I have the prerequisite headers etc in place I follow the make instructions and get a whole slew of errors (see below). WTF? Could this be a bigger nose bleed.?

Is there a simple set of instructions that will help me get thru this. Cummon here, I am a developer and I have to say that if you expect a regular joe to get this, you have another thought coming... Don't get me wrong, I think that ubuntu is the greatest thing since sliced bread, but this sort of rough edge is not conducive to recommending this to the uninitiated.

bart@savantlaptop:~/Desktop/ndiswrapper-1.52$ sudo make install
make -C driver install
make[1]: Entering directory `/home/bart/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/bart/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
echo /lib/modules/2.6.24-16-generic/misc
/lib/modules/2.6.24-16-generic/misc
mkdir -p /lib/modules/2.6.24-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-16-generic/misc
/sbin/depmod -a 2.6.24-16-generic -b /
make[1]: Leaving directory `/home/bart/Desktop/ndiswrapper-1.52/driver'
make -C utils install
make[1]: Entering directory `/home/bart/Desktop/ndiswrapper-1.52/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/bart/Desktop/ndiswrapper-1.52/utils'
make: *** [install] Error 2
bart@savantlaptop:~/Desktop/ndiswrapper-1.52$

---

### Post by kevdog on 2008-05-08
You don't have the linux-header files package installed.  To install

sudo aptitude install linux-headers-`uname -r`

---

### Post by bartt on 2008-05-08
Thank you very much. That got it compiled and installed.
Now on to configuration..

---

