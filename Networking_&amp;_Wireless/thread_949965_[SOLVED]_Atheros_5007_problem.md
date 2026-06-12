---
title: "[SOLVED] Atheros 5007 problem"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Oram on 2008-10-16
Hello, I am trying to install the driver for my Atheros 5007 in ubuntu.
I am fallowing this guide.[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

I have got my internet card to work 30 minutes earlier with this guide when I installed under windows XP(to make sure I could get my drivers working).  Now when i try to disable Atheros HAL and unchecked it and reboot it there is no check next to enabled but still says in use.  If I try to install drivers when I do sudo make this comes up.
```
ryan@ryan-laptop:~/Desktop/madwifi-hal-0.10.5.6-r3861-20080903$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: At top level:
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: In function 'main':
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode] Error 1
make[2]: *** [/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal] Error 2
make[1]: *** [_module_/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3861-20080903] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
```

If I try to continue with ```
sudo make install
``` This is what comes up. ```
ryan@ryan-laptop:~/Desktop/madwifi-hal-0.10.5.6-r3698-20080604$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: At top level:
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: In function 'main':
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode] Error 1
make[2]: *** [/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal] Error 2
make[1]: *** [_module_/home/ryan/Desktop/madwifi-hal-0.10.5.6-r3698-20080604] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

``` If I use ```
sudo modprobe ath_pci
``` Then reboot my wireless does not work.  I am using 32 bit Ubuntu and everything else works except for this so I'm guessing I need to install something or edit something because it worked before.  I think it has something to do with the Atheros HAL saying it is "In use" even though it is not checked.  Thanks for any help I can get.

---

### Post by Oram on 2008-10-16
Fixed it with what marcobra said from 
[https://answers.launchpad.net/ubuntu/+question/46770](https://answers.launchpad.net/ubuntu/+question/46770)
I guess I needed to get build-essential or just update computer than install drivers.

---

