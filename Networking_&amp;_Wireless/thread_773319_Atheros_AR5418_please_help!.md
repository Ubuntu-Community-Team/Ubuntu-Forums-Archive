---
title: "Atheros AR5418 please help!"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by jammasterstan on 2008-04-28
I think that I have read just about every post on the ubuntu forums about my particular wireless chipset and after trying every thing I still cant get my wireless working. I'm using hardy heron right now.
> 
0c:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)

there is my lspci listing for my network adapter
and when I try to use the Madwifi svn trunk I get this error when i try to make
> toxic@toxic-laptop:~/madwifi/trunk$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/toxic/madwifi/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/toxic/madwifi/trunk/ath/if_ath.o
  CC [M]  /home/toxic/madwifi/trunk/ath/if_ath_radar.o
  CC [M]  /home/toxic/madwifi/trunk/ath/if_ath_pci.o
  LD [M]  /home/toxic/madwifi/trunk/ath/ath_pci.o
  CC [M]  /home/toxic/madwifi/trunk/ath_hal/ah_os.o
  HOSTCC  /home/toxic/madwifi/trunk/ath_hal/uudecode
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/toxic/madwifi/trunk/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c: At top level:
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/toxic/madwifi/trunk/ath_hal/uudecode.c: In function 'main':
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/toxic/madwifi/trunk/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/toxic/madwifi/trunk/ath_hal/uudecode] Error 1
make[2]: *** [/home/toxic/madwifi/trunk/ath_hal] Error 2
make[1]: *** [_module_/home/toxic/madwifi/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
toxic@toxic-laptop:~/madwifi/trunk$ 


if anybody knows either where to find another driver or how to figure out how to fix the problems that im having with my current set of svn drivers any help would be good

I got this after fallowing the steps from thinkwiki
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

Any help would be greatly appreciated, and thank you in advance.

---

