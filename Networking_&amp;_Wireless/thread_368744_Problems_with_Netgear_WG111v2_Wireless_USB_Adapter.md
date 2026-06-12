---
title: "Problems with Netgear WG111v2 Wireless USB Adapter in Ubuntu Edgy Eft"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by gobr3800 on 2007-02-23
Hi,

I'm new to Ubuntu and have installed the desktop version of Edgy Eft. It seems to work fine, apart from some problems that I've been having with my wireless device.

Ubuntu is able to automatically setup the device when I enter my network's SSID and WEP key. But when I try to install updates (I've got a brand new version of Edgy Eft), the system completely freezes. I can't move the mouse, press ALT-CTRL-F2 or anything. All I can do is manually reset my system. 

I can surf the web in Firefox though it seems that when I go to certain sites, it freezes as well. For example, I was looking to configure my GRUB settings and was directed by these forums to [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm). Whenever I go to this site, my system freezes.

One last thing - the blue LED on the wireless adapter doesn't flash like it does in Windows XP.

Would appreciate any help you can give me!

---

### Post by phossal on 2007-02-23
The default driver is *experimental*. You might not *want* to, but trying ndiswrapper may solve some of your problems, once you fix the ones it creates. ;) My device operates trouble free.

---

### Post by gobr3800 on 2007-02-24
Thanks for the reply. I didn't realise that the default driver was experimental - that explains a bit!

I'm getting some errors trying to install ndiswrapper. Here's what happens when I follow the installation directions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) ...

I download the tar from [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) and extract it to a folder on my desktop.

Next, I open terminal and cd into the folder on the desktop.

I type in *sudo make distclean*. So far, so good.

Here's where I get the problem. I type in *sudo make* and things start looking like they're installing properly until I start getting a mountain of errors (see below). Any idea what I could be doing wrong?

gerard@gerard-desktop:~/Desktop/ndiswrapper-1.37$ sudo make
make -C driver
make[1]: Entering directory `/home/gerard/Desktop/ndiswrapper-1.37/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/gerard/Desktop/ndiswrapper-1.37/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /home/gerard/Desktop/ndiswrapper-1.37/driver/built-in.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/crt.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/hal.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/iw_ndis.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/loader.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/ndis.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/ntoskernel.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/ntoskernel_io.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/pe_linker.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/pnp.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/proc.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/rtl.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/wrapmem.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/wrapndis.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/wrapper.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/usb.o
  CC [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/divdi3.o
  LD [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/gerard/Desktop/ndiswrapper-1.37/driver/ndiswrapper.mod.o
  LD [M]  /home/gerard/Desktop/ndiswrapper-1.37/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/gerard/Desktop/ndiswrapper-1.37/driver'
make -C utils
make[1]: Entering directory `/home/gerard/Desktop/ndiswrapper-1.37/utils'
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
make[1]: Leaving directory `/home/gerard/Desktop/ndiswrapper-1.37/utils'
make: *** [all] Error 2

---

### Post by phossal on 2007-02-24
You need a couple of packages. You can get them via the net obviously, if you're connected, or you can pull them right off the CD. The ndiswrapper install is failing because you don't have the build-essential package installed. It seems like a catch-22. The failsafe is the install CD. You can put the cd in, and get the ndiswrapper package: ndiswrapper-utils.1.8 

Once that's installed, you just need to pick up on one of the good tutorials (like the one I wrote in my sig).

---

### Post by gobr3800 on 2007-03-08
That worked fine. Thank you so much for all your help. Sorry it has taken a while to get back to you - been quite busy lately and haven't had time to play around with Ubuntu. I think I'll be using it a lot more now.

---

### Post by phossal on 2007-03-09
You're welcome, of course. I want to make sure kvonb gets the credit he deserves. He cleared up the most significant part (among other things): the mythical 2nd chipset. Glad you're up and running! 

Regards!

---

