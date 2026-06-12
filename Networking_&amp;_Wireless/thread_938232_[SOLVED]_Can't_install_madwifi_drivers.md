---
title: "[SOLVED] Can't install madwifi drivers"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by plongo01 on 2008-10-04
I am having trouble installing madwifi drivers on my kubuntu 8.04 laptop. When I try to install the dirvers I get the following output:

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/paul/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/paul/madwifi/ath/if_ath.o
  CC [M]  /home/paul/madwifi/ath/if_ath_pci.o
  LD [M]  /home/paul/madwifi/ath/ath_pci.o
  CC [M]  /home/paul/madwifi/ath_hal/ah_os.o
  HOSTCC  /home/paul/madwifi/ath_hal/uudecode
/home/paul/madwifi/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/paul/madwifi/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/paul/madwifi/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/paul/madwifi/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/paul/madwifi/ath_hal/uudecode.c: At top level:
/home/paul/madwifi/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/paul/madwifi/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/paul/madwifi/ath_hal/uudecode.c: In function 'main':
/home/paul/madwifi/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/paul/madwifi/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/paul/madwifi/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/paul/madwifi/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/paul/madwifi/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/paul/madwifi/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/paul/madwifi/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/paul/madwifi/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/paul/madwifi/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/paul/madwifi/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/paul/madwifi/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/paul/madwifi/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/paul/madwifi/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/paul/madwifi/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/paul/madwifi/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/paul/madwifi/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/paul/madwifi/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/paul/madwifi/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/paul/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/paul/madwifi/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/paul/madwifi/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/paul/madwifi/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/paul/madwifi/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/paul/madwifi/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/paul/madwifi/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/paul/madwifi/ath_hal/uudecode] Error 1
make[2]: *** [/home/paul/madwifi/ath_hal] Error 2
make[1]: *** [_module_/home/paul/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

Can anyone help me? Also I do not have any internet access on that laptop at all. Alot of solutions include using apt-get or installing a package. Unless there is a way to do that without internet access that I am aware of. For example when I attempt apt-get install build-essential it tells me that package doesn't exist.

---

### Post by plongo01 on 2008-10-05
I was able to get the madwifi drivers installed by installing the build-essential package from the live cd. However, my wifi is still not working. I have checked out all the wikis and when I get to the part where you have to do ifconfig ath0 up I get the following error:

ath0: no such device

Does anyone have a solution please? I really need my wireless to work.

---

### Post by plongo01 on 2008-10-05
Nevermind I figured it out myself. Had to add ath_pci to /etc/modules.

---

