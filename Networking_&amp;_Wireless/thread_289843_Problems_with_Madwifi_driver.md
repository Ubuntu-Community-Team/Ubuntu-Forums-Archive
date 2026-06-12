---
title: "Problems with Madwifi driver"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by anonymoususername on 2006-10-31
OK, so I know that Madwifi should apparently "just work" in Edgy, but it doesn't appear to, or at least my Wireless card doesn't appear in Networking. So I downloaded madwifi-0.9.2, but when I try to run the make command I get a gigantic cascade of errors, any suggestions? I searched the madwifi wiki and found nothing. For the record, the errors are:

```
$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/agony/download/madwifi-0.9.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  HOSTCC  /home/agony/download/madwifi-0.9.2/ath/uudecode
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:27:19: error: errno.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:29:20: error: string.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/agony/download/madwifi-0.9.2/ath/uudecode.c: In function 'uudecode_usage':
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c: At top level:
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:40: error: expected ')' before '*' token
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:70: error: expected ')' before '*' token
/home/agony/download/madwifi-0.9.2/ath/uudecode.c: In function 'main':
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:121: error: for each function it appears in.)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:188: warning: implicit declaration of function 'open'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/agony/download/madwifi-0.9.2/ath/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/agony/download/madwifi-0.9.2/ath/uudecode] Error 1
make[2]: *** [/home/agony/download/madwifi-0.9.2/ath] Error 2
make[1]: *** [_module_/home/agony/download/madwifi-0.9.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [modules] Error 2

```

I had it working before on my 64 bit install of Ubuntu, although I couldn't see any access points, but I could at least make the driver, now that I've switched to the i386 version of Edgy it doesn't seem to work at all.

---

### Post by anonymoususername on 2006-10-31
Yeah, so if there's any other information you guys need, I'm happy to provide it.

---

### Post by anonymoususername on 2006-11-01
Bump. Any suggestions? I'm getting pretty sick and tired of trying to get my wireless card to work...

---

### Post by zdomjus on 2006-11-01
hello anonymoususername. i have installed madwifi driver on a very old notebook (dell latitude cpi-r pentium II processor 400MHz) and my atheros chipset based wi-fi card works fine. have you installed the _'build essential'_ package before compiling? it contains all you need to compile drivers without errors. in my case the wi-fi card was seen but not was not recognized during alternate (textual) install of edgy eft, so after rebooting i couldn't find it in system -> administration -> network. after having compiled madwifi drivers it was correctly displayed in network options with the WEP keys I entered during installation.

---

### Post by anonymoususername on 2006-11-01
OK, thanks, I installed the "build essential" package and it seems to have worked, figures it would be something simple like that. Thanks!

---

