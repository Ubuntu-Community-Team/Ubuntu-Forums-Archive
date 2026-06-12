---
title: "Madwifi Macbook Not Working"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by deaddylan123 on 2007-10-13
Hello.

I recently installed ubuntu on my macbook and am trying to get the wireless working following the guide in the ubuntu wiki, however, whenever i get to the 'make' and 'sudo make install' step,  i get some error message.

```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/jmartino/madwifi-ng-r2695-20070829 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  HOSTCC  /home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c: At top level:
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c: In function 'main':
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/jmartino/madwifi-ng-r2695-20070829/ath_hal/uudecode] Error 1
make[2]: *** [/home/jmartino/madwifi-ng-r2695-20070829/ath_hal] Error 2
make[1]: *** [_module_/home/jmartino/madwifi-ng-r2695-20070829] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

```

THANKS!

---

### Post by deaddylan123 on 2007-10-14
hello?????

---

### Post by UMDGaara on 2007-10-17
You must install the build-essential package

```
$ sudo apt-get install build-essential
```

---

