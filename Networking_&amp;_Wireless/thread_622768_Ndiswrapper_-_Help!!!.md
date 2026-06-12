---
title: "Ndiswrapper - Help!!!"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by Izecream on 2007-11-25
I am a newbie and I am trying to install a driver working for windows with NDISWRAPPER.

I don't know what you need to know to help so here is the whole terminalprompt

Some of it is danish but I hope the english stuff is enough

loadndisdriver.c:150: fejl: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: fejl: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: fejl: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: advarsel: implicit declaration of function ‘lstat’
loadndisdriver.c:158: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: fejl: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: advarsel: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: advarsel: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: advarsel: implicit declaration of function ‘fopen’
loadndisdriver.c:178: fejl: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: advarsel: implicit declaration of function ‘fgets’
loadndisdriver.c:194: advarsel: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: advarsel: implicit declaration of function ‘fclose’
loadndisdriver.c:150: advarsel: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: advarsel: implicit declaration of function ‘tolower’
loadndisdriver.c:221: advarsel: implicit declaration of function ‘chdir’
loadndisdriver.c:222: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: fejl: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: advarsel: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: advarsel: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: advarsel: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: fejl: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: fejl: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: fejl: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: fejl: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: fejl: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: advarsel: implicit declaration of function ‘opendir’
loadndisdriver.c:267: advarsel: implicit declaration of function ‘malloc’
loadndisdriver.c:267: advarsel: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: advarsel: implicit declaration of function ‘memset’
loadndisdriver.c:271: advarsel: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: advarsel: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: advarsel: implicit declaration of function ‘readdir’
loadndisdriver.c:280: advarsel: assignment makes pointer from integer without a cast
loadndisdriver.c:282: fejl: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:287: advarsel: implicit declaration of function ‘stat’
loadndisdriver.c:287: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:288: advarsel: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:294: advarsel: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:296: advarsel: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:299: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:302: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:303: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:305: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:311: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:312: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:313: advarsel: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: advarsel: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:317: fejl: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: fejl: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:282: advarsel: unused variable ‘statbuf’
loadndisdriver.c:344: fejl: expected expression before ‘struct’
loadndisdriver.c:346: advarsel: implicit declaration of function ‘closedir’
loadndisdriver.c:348: advarsel: implicit declaration of function ‘free’
loadndisdriver.c:355: advarsel: implicit declaration of function ‘munmap’
loadndisdriver.c:355: fejl: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: fejl: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: fejl: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: fejl: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: fejl: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: fejl: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: advarsel: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: advarsel: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: advarsel: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: advarsel: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: fejl: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: fejl: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: advarsel: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: fejl: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: fejl: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: advarsel: assignment makes pointer from integer without a cast
loadndisdriver.c:435: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:436: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:439: fejl: forsøg på at følge en henvisning til en variabel af en ufuldstændig type
loadndisdriver.c:447: fejl: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: fejl: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: fejl: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: advarsel: implicit declaration of function ‘strstr’
loadndisdriver.c:472: advarsel: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: advarsel: implicit declaration of function ‘strtol’
loadndisdriver.c:473: fejl: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: advarsel: implicit declaration of function ‘unlink’
loadndisdriver.c:489: advarsel: implicit declaration of function ‘mknod’
loadndisdriver.c:489: fejl: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: fejl: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: fejl: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: fejl: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: advarsel: implicit declaration of function ‘openlog’
loadndisdriver.c:511: fejl: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: fejl: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: fejl: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: fejl: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: fejl: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: advarsel: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: advarsel: implicit declaration of function ‘printf’
loadndisdriver.c:517: advarsel: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: advarsel: implicit declaration of function ‘atoi’
loadndisdriver.c:542: advarsel: implicit declaration of function ‘atof’
loadndisdriver.c:549: advarsel: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: advarsel: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: advarsel: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Fejl 1
make[1]: Forlader katalog '/home/dennis/ndiswrapper-1.49/utils'
make: *** [all] Fejl 2
dennis@dennis-desktop:~/ndiswrapper-1.49$ make install
make -C driver install
make[1]: Går til katalog '/home/dennis/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/dennis/ndiswrapper-1.49/driver
make[2]: Går til katalog '/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Forlader katalog '/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
mkdir: kan ikke oprette katalog '/lib/modules/2.6.22-14-generic/misc': Permission denied
make[1]: *** [install] Fejl 1
make[1]: Forlader katalog '/home/dennis/ndiswrapper-1.49/driver'
make: *** [install] Fejl 2
dennis@dennis-desktop:~/ndiswrapper-1.49$ run make install
bash: run: command not found
dennis@dennis-desktop:~/ndiswrapper-1.49$ make install
make -C driver install
make[1]: Går til katalog '/home/dennis/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/dennis/ndiswrapper-1.49/driver
make[2]: Går til katalog '/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Forlader katalog '/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
mkdir: kan ikke oprette katalog '/lib/modules/2.6.22-14-generic/misc': Permission denied
make[1]: *** [install] Fejl 1
make[1]: Forlader katalog '/home/dennis/ndiswrapper-1.49/driver'
make: *** [install] Fejl 2
dennis@dennis-desktop:~/ndiswrapper-1.49$

---

