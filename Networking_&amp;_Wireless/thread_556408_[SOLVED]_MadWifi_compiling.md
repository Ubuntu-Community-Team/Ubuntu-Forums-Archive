---
title: "[SOLVED] MadWifi compiling"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by scruffybeard on 2007-09-21
Okie dokie,

I've been trying to get MadWifi-ng working on my Ubuntu system in order to test WEP security in one of my classes. I used svn to get the latest source, and wget to get the patch that I needed. When I try to do a make, I get a few errors and I have no idea where to go from there. Here's the terminal output from the make.

[B]scruffybeard@VaioPirate:~$ cd madwifi-ng
scruffybeard@VaioPirate:~/madwifi-ng$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/scruffybeard/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  HOSTCC  /home/scruffybeard/madwifi-ng/ath_hal/uudecode
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c: At top level:
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c: In function 'main':
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/scruffybeard/madwifi-ng/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/scruffybeard/madwifi-ng/ath_hal/uudecode] Error 1
make[2]: *** [/home/scruffybeard/madwifi-ng/ath_hal] Error 2
make[1]: *** [_module_/home/scruffybeard/madwifi-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2
scruffybeard@VaioPirate:~/madwifi-ng$[/B]

Anyone got some ideas that might help? Thanks!

---

### Post by bjd on 2007-09-21
I think you're missing the libc6-dev package

---

### Post by spd106 on 2007-09-21
Have you installed the build-essential and linux-headers packages?

---

### Post by kevdog on 2007-09-21
Do the following:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Those are backticks and not quotes

---

### Post by scruffybeard on 2007-09-21
> **bjd said:**
> I think you're missing the libc6-dev package

My friend, this was mos def my problem. Thank you so much for your help. This was for a bonus assignment in my networking and securities class, and my instructor refused to help us until after someone completed the assignment.

With your help, this will definitely put me on the right track well ahead of the rest of the class. So again, thank you so much for your assistance.:guitar:

---

### Post by scruffybeard on 2007-09-21
> **kevdog said:**
> Do the following:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Those are backticks and not quotes

This is also a pretty good idea, and I'll fire up the code in a bit. Right now though, there is a good ep of Futurama calling to me from the quads. Thanks for your help, I'll let everyone know how the WEP test goes once I get aircrack working.

---

