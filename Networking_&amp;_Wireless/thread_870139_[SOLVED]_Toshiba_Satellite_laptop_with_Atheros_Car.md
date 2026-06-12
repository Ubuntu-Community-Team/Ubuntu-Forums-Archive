---
title: "[SOLVED] Toshiba Satellite laptop with Atheros Card - won't connect"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by markab9569 on 2008-07-25
I am having trouble getting my Toshiba wireless card to connect.

I went here and followed the instructions:
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

and got he following error messages:


mark@mark-laptop:~$ cd Desktop
mark@mark-laptop:~/Desktop$ cd madwifi-hal-0.10.5.6-r3772-20080716/
mark@mark-laptop:~/Desktop/madwifi-hal-0.10.5.6-r3772-20080716$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  HOSTCC  /home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c: At top level:
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c: In function 'main':
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal/uudecode] Error 1
make[2]: *** [/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716/ath_hal] Error 2
make[1]: *** [_module_/home/mark/Desktop/madwifi-hal-0.10.5.6-r3772-20080716] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
mark@mark-laptop:~/Desktop/madwifi-hal-0.10.5.6-r3772-20080716$ 
mark@mark-laptop:~/Desktop/madwifi-hal-0.10.5.6-r3772-20080716$ 

does anybody have any insights?

---

### Post by terry slaughter on 2008-07-25
The first place to check is if you used "sudo" before using "make",I have forgot to do this many times and have seen similar outputs.Second check that
your restricted hardware is "enabled"& "In use" under Administration /Hardware Drivers. My Atheros wifi has an activate support check box.

---

### Post by markab9569 on 2008-07-26
I can confirm that I did use sudo before make.

I am a real newbie to this, and I am starting to get confused. One of my problems is that I can not even get the computer to attach through the ethernet connection. The computer recognizes the network, but still will not connect to the internet

---

### Post by terry slaughter on 2008-07-26
Do you have any encryption on your network? If you can see the networks ESS ID than the hardware is working.

---

### Post by chili555 on 2008-07-26
> stdio.h: No such file or directoryLooks like you may not have *build-essential* installed.

---

### Post by markab9569 on 2008-07-27
can you tell me where I can download a copy of build essential?

---

### Post by terry slaughter on 2008-07-27
You can find build-essential under ADMIN>Synaptic Package Manager.You can use Search, then click the box.

---

### Post by markab9569 on 2008-07-27
Build-essential is not on the list

---

### Post by chili555 on 2008-07-28
In Synaptic, go to Settings -> Repositories and enable your CD. The CD needs to be in the tray when you do this. Press 'Reload' and look for build-essential again. Install it and then go back to your madwifi directory and try 'make' again.

---

### Post by markab9569 on 2008-07-29
That did it I am online thanks a lot.

---

