---
title: "Belkin Wireless Card on 6.06 with ndiswrapper"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by omarello on 2006-10-03
Hello,

I was trying to connect my laptop the internet, i have  belikin pcmcia card and i installed ubuntu 6.06 yesterday, but it doesn't seem to work.

I follow instructions on how to use ndiswrapper to fix that, and the article suggested i build ndiswrapper from sources as it seems that this card only works with version 1.23, so i uninstalled ndiswrapper completley following the guidelines from the ndiswrapper Wiki.. and tried to build from sources... but it doens't seem to compile although i followed the exact same instructions...

i am really new to this and i don't understand everything but by looking at the error it seems that the compiler cannot find the std c libraries or somthing... neways below are the error messages hope you guys can help.

Also i am really sorry if this was asked a million times, but i just can't get it to work... i am a complete noob and its my first install of ubuntu... also i figured i will get more specific help if i asked the question here rather than the ndiswrapper forums on sourceforge.

neways i issued the following command on the sources directory of ndiswrapper

```
sudo make
```

and here is what i get

```

make -C driver
make[1]: Entering directory `/home/omarello/ndiswrapper-1.23/driver'
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/omarello/ndiswrapper-1.23/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: Leaving directory `/home/omarello/ndiswrapper-1.23/driver'
make -C utils
make[1]: Entering directory `/home/omarello/ndiswrapper-1.23/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: syntax error before ‘size_t’
../driver/loader.h:24: warning: no semicolon at end of struct or union
../driver/loader.h:26: error: syntax error before ‘}’ token
../driver/loader.h:52: error: array type has incomplete element type
../driver/loader.h:56: error: array type has incomplete element type
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: syntax error before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c:95: error: dereferencing pointer to incomplete type
loadndisdriver.c:96: error: dereferencing pointer to incomplete type
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:159: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:162: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:162: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:214: error: storage size of ‘driver_file’ isn’t known
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: syntax error before ‘struct’
loadndisdriver.c:214: warning: unused variable ‘driver_file’
loadndisdriver.c:236: warning: control reaches end of non-void function
loadndisdriver.c: At top level:
loadndisdriver.c:237: error: syntax error before ‘return’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:251: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:253: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:261: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:263: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:269: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:269: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:273: warning: implicit declaration of function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:282: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:282: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:284: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:286: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:286: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function ‘stat’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:284: warning: unused variable ‘statbuf’
loadndisdriver.c:347: error: syntax error before ‘struct’
loadndisdriver.c:349: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:351: warning: implicit declaration of function ‘free’
loadndisdriver.c:358: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:364: warning: control reaches end of non-void function
loadndisdriver.c: At top level:
loadndisdriver.c:383: error: syntax error before ‘*’ token
loadndisdriver.c: In function ‘add_driver_devices’:
loadndisdriver.c:389: error: ‘from’ undeclared (first use in this function)
loadndisdriver.c:390: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:390: error: ‘driver_name’ undeclared (first use in this function)
loadndisdriver.c:391: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:391: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:396: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:405: error: dereferencing pointer to incomplete type
loadndisdriver.c:406: error: dereferencing pointer to incomplete type
loadndisdriver.c:409: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:409: error: dereferencing pointer to incomplete type
loadndisdriver.c:410: error: dereferencing pointer to incomplete type
loadndisdriver.c:411: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:415: error: dereferencing pointer to incomplete type
loadndisdriver.c:416: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:421: error: dereferencing pointer to incomplete type
loadndisdriver.c:421: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:425: error: ‘devices’ undeclared (first use in this function)
loadndisdriver.c:427: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:448: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:450: error: dereferencing pointer to incomplete type
loadndisdriver.c:452: warning: implicit declaration of function ‘strncat’
loadndisdriver.c:452: warning: incompatible implicit declaration of built-in function ‘strncat’
loadndisdriver.c:411: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_all_devices’:
loadndisdriver.c:472: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:474: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:474: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:474: error: ‘driver’ undeclared (first use in this function)
loadndisdriver.c:474: warning: left-hand operand of comma expression has no effect
loadndisdriver.c:474: warning: statement with no effect
loadndisdriver.c:480: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:482: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:484: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:490: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:496: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:497: error: dereferencing pointer to incomplete type
loadndisdriver.c:498: error: dereferencing pointer to incomplete type
loadndisdriver.c:501: error: dereferencing pointer to incomplete type
loadndisdriver.c:502: warning: implicit declaration of function ‘S_ISDIR’
loadndisdriver.c:504: error: dereferencing pointer to incomplete type
loadndisdriver.c:505: error: dereferencing pointer to incomplete type
loadndisdriver.c:509: error: dereferencing pointer to incomplete type
loadndisdriver.c:510: error: dereferencing pointer to incomplete type
loadndisdriver.c:515: error: dereferencing pointer to incomplete type
loadndisdriver.c:531: error: syntax error before ‘struct’
loadndisdriver.c:472: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:552: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:552: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:560: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:560: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:561: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:561: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:571: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:571: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:576: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:577: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:577: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:577: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:579: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:584: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:605: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:605: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:605: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:605: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:605: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:607: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:609: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:611: warning: implicit declaration of function ‘printf’
loadndisdriver.c:611: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:621: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:636: warning: implicit declaration of function ‘atof’
loadndisdriver.c:668: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/omarello/ndiswrapper-1.23/utils'
make: *** [all] Error 2

```

---

### Post by omarello on 2006-10-03
ok so i managed to get it to compile. i guess i was missing some packages... i installed a bunch and i am still not sure which ones was i missing anyways the good thing is that ndiswrapper is working now and it recognizes my ccard and it also found the my wireless network at home..

but one thing still not working is that setting to dhcp doesn't work... i dunno why i can't receive an ip address or somthing but whenever i select the dhcp option i can't use the wlan1 in the connections instead of lo...

when i set to static ip i get wlan1 in the connections list but i can't connect to the internet...

what could i have done wrong now???

please check image to see what i mean

thanks for your help

---

### Post by omarello on 2006-10-04
bump...

it seems like most people have the same problems round here :(

---

### Post by Fitzcarraldo on 2006-10-07
Which model of Belkin PCMCIA card are you using, *omarello*? Is it the Belkin 54g Notebook PCMCIA Wireless Card, model no. F5D7010? If so, the following thread may be of help:

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

Good luck!

---

### Post by phoenixthesmeg on 2006-10-17
Hey I just had the same problem in kubuntu trying to compile madwifi. I then installed g++ and with it came the base kernel headers. Not sure if the headers is what was missing or wether it needed g++ but seems to have worked well.

Just thought I would add that extra bit of help.

---

