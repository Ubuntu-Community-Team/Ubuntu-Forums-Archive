---
title: "Can't connect to wireless network"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by hotel86 on 2008-06-22
I have a dual boot Vista/Xubuntu Toshiba Satelite AMD Turion 64 x2 with the Aethos Wireless Adapter and I cant even see the wireless networks or an option for connecting to one. is there a network driver or specific wireless networking/connection program I should use?

---

### Post by cooltd825 on 2008-06-22
I'm assuming it works with Vista, right?

if so, then try using this

 [http://madwifi.org/wiki](http://madwifi.org/wiki)

---

### Post by hotel86 on 2008-06-22
Yes it does work with Vista.  Keep getting this error message when I try to install madwifi:
    Failed to mount udf volume
    mount: block device /dev/hda is write protected mounting read     only 
    mount: wrong fs type, bad option, bad superblock on /dev/hda,     missing code pageor helper program, or other error in some cases     useful info is found in syslog- try dmesg| tail or so

I did try to find syslog but couldnt

---

### Post by hotel86 on 2008-06-23
When I run the terminal and run the make command I get this returned:

hotel@hotel-laptop:~/Desktop/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/hotel/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/hotel/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/hotel/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/hotel/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/hotel/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/hotel/Desktop/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/hotel/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/hotel/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
hotel@hotel-laptop:~/Desktop/madwifi-0.9.4$

---

### Post by lisati on 2008-06-23
You might have to install the "build-essential" package. It can be done from the terminal with the following command:
```
sudo apt-get build-essential
```

---

