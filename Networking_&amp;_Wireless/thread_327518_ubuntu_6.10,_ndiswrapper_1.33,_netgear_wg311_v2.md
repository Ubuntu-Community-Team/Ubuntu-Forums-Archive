---
title: "ubuntu 6.10, ndiswrapper 1.33, netgear wg311 v2"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by lauraj on 2006-12-29
I have the linux headers installed, but still get these errors when trying to install ndiswrapper:

laura@frappuccino:~/Desktop/ndiswrapper/ndiswrapper-1.33$ sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/laura/Desktop/ndiswrapper/ndiswrapper-1.33/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/laura/Desktop/ndiswrapper/ndiswrapper-1.33/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/laura/Desktop/ndiswrapper/ndiswrapper-1.33/driver'
make -C utils install
make[1]: Entering directory `/home/laura/Desktop/ndiswrapper/ndiswrapper-1.33/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
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
loadndisdriver.c:179: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:179: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:206: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:218: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:218: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:222: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:223: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:225: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:233: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:250: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:250: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:252: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:256: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:258: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:260: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:268: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:272: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:281: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:319: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:345: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:347: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:349: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:356: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:356: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:368: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:371: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:371: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:375: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:368: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:420: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:420: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:424: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:427: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:428: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:430: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:466: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:466: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:475: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:475: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:485: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:485: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:491: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:491: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:491: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:492: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:497: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:513: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:513: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:515: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:519: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:529: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:544: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:551: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:592: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/laura/Desktop/ndiswrapper/ndiswrapper-1.33/utils'
make: *** [install] Error 2
laura@frappuccino:~/Desktop/ndiswrapper/ndiswrapper-1.33$ 


laura@frappuccino:~/Desktop/ndiswrapper/ndiswrapper-1.33$ sudo apt-get install linux-headers-2.6.17-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by c.dric on 2006-12-29
and when you ran 'make' at the previous step, it didn't return any errors ?

i followed the steps in the 2nd post of [this thread]("http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper") and it worked fine.

i would give it another shot ... starting at 

make distclean

to clean previous attempts.

---

### Post by lauraj on 2006-12-29
thanks.... installing build-essentials got ndiswrapper to install. Then I attempted to install my wg311v2.inf driver that I copied from the cd using

ndiswrapper -i wg311v2.inf

but it said it was missing some files and that it may be incomplete. I found the additional files on the cd. But when I tried to remove the driver so I could re-install it said it couldn't find the directory. But if i tried to install the driver again, it said it was already installed. Finally I just removed the directory it was complaining about (/etc/ndiswrapper/wg311v2 I think it was). Then I ran the above command again, and it seemed to install (no errors, nothing). But when I run iwconfig there are no wireless extensions. IT doesnt even seem to see my wireless card anymore.... it did before.. is it because I moved the acx drivers (as mentioned in [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu"))

---

### Post by c.dric on 2006-12-29
with this command you can check which driver(s) are installed in ndiswrapper :

**sudo ndiswrapper -l** 

if you want to re-install a driver, you have to remove it first using this 

**sudo ndiswrapper -e <name of the driver as listed by the previous command>**

unload ndiswrapper (maybe it's not loaded yet)

**sudo modprobe -r ndiswrapper**

(Re)Install with this command 

**sudo ndiswrapper -i <name of the win driver>.inf**

make sure all the driver files ( .sys, .dll, .cat ...) are in the same folder as the .inf file.
make sure the folder, the case, the filename and the extension are correct or it won't work.

Check if the driver is installed properly.

**sudo ndiswrapper -l **

if you get ".... driver present, hardware present" it's good.

Load the ndiswrapper module 

**sudo modprobe ndiswrapper**

no output is good.

**sudo ndiswrapper -m**

should load ndiswrapper at boot.

**iwconfig**  

should show if you have a wireless interface up

---

### Post by lauraj on 2006-12-29
ok I think I got it working now. I moved the acx drivers back to where they came from, and I also did this part of that thread:

> Next, there are a couple of bugs to work around:

Code:

gedit /etc/modules

and insert this line at the end:
Code:

ndiswrapper

Then:
Code:

gedit /etc/init.d/wireless-network.sh

and place this line in the file:
Code:

/etc/init.d/networking restart

then make it executable:
Code:

chmod +x /etc/init.d/wireless-network.sh

and Finally, create a symlink pointing to it:
Code:

ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S42wireless-network



then rebooted, and it connected to the open wireless network automatically. So either one of both of those steps got it to work, not sure which one. thanks for your help

---

