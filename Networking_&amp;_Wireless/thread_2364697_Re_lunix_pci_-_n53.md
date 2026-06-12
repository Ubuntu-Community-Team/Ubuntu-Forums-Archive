---
title: "Re: lunix pci - n53"
date: 2017-06-26
forum: Networking &amp; Wireless
---

### Post by 101kitty on 2017-06-26
```
 raynskitty@raynskitty-H81M-S2PV:~$ sudo apt-get update
[sudo] password for raynskitty: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Fetched 306 kB in 0s (486 kB/s)                                    
Reading package lists... Done
raynskitty@raynskitty-H81M-S2PV:~$ sudo apt-get upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raynskitty@raynskitty-H81M-S2PV:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-$(uname -r) -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
linux-headers-4.8.0-36-generic is already the newest version (4.8.0-36.36~16.04.1).
linux-headers-generic is already the newest version (4.4.0.81.87).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raynskitty@raynskitty-H81M-S2PV:~$ cd
raynskitty@raynskitty-H81M-S2PV:~$ cd~
No command 'cd~' found, did you mean:
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdi' from package 'cdo' (universe)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cde' from package 'cde' (universe)
cd~: command not found
raynskitty@raynskitty-H81M-S2PV:~$ cd ~
raynskitty@raynskitty-H81M-S2PV:~$ git clone https://github.com/mareksuscak/asus-pce-n53-linux.git
fatal: destination path 'asus-pce-n53-linux' already exists and is not an empty directory.
raynskitty@raynskitty-H81M-S2PV:~$ cd asus-pce-n53-linux
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make
make -C tools
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/tools'
/home/raynskitty/asus-pce-n53-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/raynskitty/asus-pce-n53-linux/os/linux/Makefile
make -C /lib/modules/4.8.0-36-generic/build SUBDIRS=/home/raynskitty/asus-pce-n53-linux/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-36-generic'
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:558:72: error: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:578:72: error: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o' failed
make[2]: *** [/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o] Error 1
Makefile:1491: recipe for target '_module_/home/raynskitty/asus-pce-n53-linux/os/linux' failed
make[1]: *** [_module_/home/raynskitty/asus-pce-n53-linux/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'
Makefile:384: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ make
make -C tools
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/tools'
/home/raynskitty/asus-pce-n53-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/raynskitty/asus-pce-n53-linux/os/linux/Makefile
make -C /lib/modules/4.8.0-36-generic/build SUBDIRS=/home/raynskitty/asus-pce-n53-linux/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-36-generic'
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:558:72: error: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:578:72: error: passing argument 3 of ‘pci_read_config_word’ from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG * {aka long unsigned int *}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: At top level:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:741:1: fatal error: opening dependency file /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/.rtmp_mcu.o.d: Permission denied
 }
 ^
cc1: some warnings being treated as errors
compilation terminated.
scripts/Makefile.build:289: recipe for target '/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o' failed
make[2]: *** [/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o] Error 1
Makefile:1491: recipe for target '_module_/home/raynskitty/asus-pce-n53-linux/os/linux' failed
make[1]: *** [_module_/home/raynskitty/asus-pce-n53-linux/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'
Makefile:384: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ 


```


what did i do wrong, i did tried installing it more than one time.

Another attempt failed

```
 raynskitty@raynskitty-H81M-S2PV:~$ sudo apt install git -y && sudo git clone https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10.git /opt/asus-n53-driver
[sudo] password for raynskitty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.7.4-0ubuntu1.1).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Cloning into '/opt/asus-n53-driver'...
remote: Counting objects: 344, done.
remote: Total 344 (delta 0), reused 0 (delta 0), pack-reused 344
Receiving objects: 100% (344/344), 2.85 MiB | 0 bytes/s, done.
Resolving deltas: 100% (125/125), done.
Checking connectivity... done.
raynskitty@raynskitty-H81M-S2PV:~$ sudo apt install build-essential linux-headers-generic linux-headers-$(uname -r) -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
linux-headers-4.8.0-36-generic is already the newest version (4.8.0-36.36~16.04.1).
linux-headers-generic is already the newest version (4.4.0.81.87).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raynskitty@raynskitty-H81M-S2PV:~$ cd /opt/asus-n53-driver
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo make
make -C tools
make[1]: Entering directory '/opt/asus-n53-driver/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/opt/asus-n53-driver/tools'
/opt/asus-n53-driver/tools/bin2h
cp -f os/linux/Makefile.6 /opt/asus-n53-driver/os/linux/Makefile
make -C /lib/modules/4.8.0-36-generic/build SUBDIRS=/opt/asus-n53-driver/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-36-generic'
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/crypt_md5.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/crypt_sha2.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/crypt_hmac.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/crypt_aes.o
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/include/crypt_aes.h:31,
                 from /opt/asus-n53-driver/os/linux/../../common/crypt_aes.c:28:
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c:1459:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c:1459:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c:1554:32: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/crypt_aes.c:1554:6: note: in expansion of macro ‘DBGPRINT’
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/crypt_arc4.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/mlme.o
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/mlme.c:28:
/opt/asus-n53-driver/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/opt/asus-n53-driver/os/linux/../../common/mlme.c:527:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/opt/asus-n53-driver/include/os/rt_linux.h:477:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/opt/asus-n53-driver/os/linux/../../common/mlme.c:528:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/opt/asus-n53-driver/include/os/rt_linux.h:477:76: note: in definition of macro ‘NdisZeroMemory’
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
In file included from /opt/asus-n53-driver/include/chip/mac_pci.h:33:0,
                 from /opt/asus-n53-driver/include/rtmp_chip.h:37,
                 from /opt/asus-n53-driver/include/rt_config.h:38,
                 from /opt/asus-n53-driver/os/linux/../../common/mlme.c:28:
/opt/asus-n53-driver/os/linux/../../common/mlme.c: In function ‘RTMPAdjustFrequencyOffset’:
/opt/asus-n53-driver/include/chip/rtmp_phy.h:583:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘FreqOffset’ will never be NULL [-Waddress]
  if (_pVal1 != NULL)        \
             ^
/opt/asus-n53-driver/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
/opt/asus-n53-driver/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘HighCurrentBit’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/opt/asus-n53-driver/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_wep.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/action.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_data.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rtmp_init.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_tkip.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_aes.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_sync.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/eeprom.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_sanity.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_info.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_cfg.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_wpa.o
/opt/asus-n53-driver/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/opt/asus-n53-driver/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_radar.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/spectrum.o
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/spectrum.c:28:
/opt/asus-n53-driver/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/opt/asus-n53-driver/os/linux/../../common/spectrum.c:1972:29: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rtmp_timer.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rt_channel.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_profile.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_asic.o
/opt/asus-n53-driver/os/linux/../../common/cmm_asic.c: In function ‘AsicGetAutoAgcOffsetForTemperatureSensor’:
/opt/asus-n53-driver/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_T
                            ^
/opt/asus-n53-driver/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_T
                            ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_cmd.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/ps.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/uapsd.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_profile.o
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../os/linux/rt_profile.c:28:
/opt/asus-n53-driver/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/opt/asus-n53-driver/os/linux/../../os/linux/rt_profile.c:411:35: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
                                   ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../os/linux/rt_profile.c:411:9: note: in expansion of macro ‘DBGPRINT’
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
         ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../chips/rtmp_chip.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/assoc.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/auth.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/auth_rsp.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/sync.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/sanity.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/rtmp_data.o
/opt/asus-n53-driver/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/opt/asus-n53-driver/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/opt/asus-n53-driver/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/connect.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/wpa.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/sta_cfg.o
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../sta/sta_cfg.c:29:
/opt/asus-n53-driver/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/opt/asus-n53-driver/os/linux/../../sta/sta_cfg.c:3954:30: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../sta/sta_cfg.c:3954:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rt_os_util.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_linux.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/ba_action.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../sta/dls.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rt_led.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/cmm_data_pci.o
/opt/asus-n53-driver/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPFreeTXDUponTxDmaDone’:
/opt/asus-n53-driver/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
/opt/asus-n53-driver/os/linux/../../common/cmm_data_pci.c: In function ‘RTMPHandleMgmtRingDmaDoneInterrupt’:
/opt/asus-n53-driver/os/linux/../../common/cmm_data_pci.c:735:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_rbus_pci_drv.o
/opt/asus-n53-driver/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function ‘RTMPInitPCIeDevice’:
/opt/asus-n53-driver/os/linux/../../os/linux/rt_rbus_pci_drv.c:1382:23: warning: unused variable ‘Index’ [-Wunused-variable]
   UINT32 MacCsr0 = 0, Index= 0;
                       ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/ee_prom.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/frq_cal.o
In file included from ./include/linux/list.h:8:0,
                 from ./include/linux/module.h:9,
                 from /opt/asus-n53-driver/include/os/rt_linux.h:31,
                 from /opt/asus-n53-driver/include/rtmp_os.h:44,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/frq_cal.c:28:
/opt/asus-n53-driver/os/linux/../../common/frq_cal.c: In function ‘FrequencyCalibrationMode’:
./include/linux/kernel.h:742:17: warning: comparison of distinct pointer types lacks a cast
  (void) (&_min1 == &_min2);  \
                 ^
/opt/asus-n53-driver/os/linux/../../common/frq_cal.c:128:13: note: in expansion of macro ‘min’
   RFValue = min(RFValue, 0x5F);
             ^
In file included from /opt/asus-n53-driver/include/chip/mac_pci.h:33:0,
                 from /opt/asus-n53-driver/include/rtmp_chip.h:37,
                 from /opt/asus-n53-driver/include/rt_config.h:38,
                 from /opt/asus-n53-driver/os/linux/../../common/frq_cal.c:28:
/opt/asus-n53-driver/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘RfReg’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/opt/asus-n53-driver/include/chip/rtmp_phy.h:592:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/opt/asus-n53-driver/os/linux/../../common/frq_cal.c:141:3: note: in expansion of macro ‘RF_M_WRITE8’
   RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);  
   ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/ee_efuse.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.o
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicSendCommandToMcu’:
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:558:72: warning: passing argument 3 of ‘pci_read_config_word’ makes pointer from integer without a cast [-Wint-conversion]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, Configurati
                                                                     ^
In file included from /opt/asus-n53-driver/include/os/rt_linux.h:41:0,
                 from /opt/asus-n53-driver/include/rtmp_os.h:44,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG {aka long unsigned int}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:28:
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:564:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:578:72: warning: passing argument 3 of ‘pci_read_config_word’ makes pointer from integer without a cast [-Wint-conversion]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, Configurati
                                                                     ^
In file included from /opt/asus-n53-driver/include/os/rt_linux.h:41:0,
                 from /opt/asus-n53-driver/include/rtmp_os.h:44,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected ‘u16 * {aka short unsigned int *}’ but argument is of type ‘ULONG {aka long unsigned int}’
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /opt/asus-n53-driver/include/rtmp_os.h:44:0,
                 from /opt/asus-n53-driver/include/rtmp_comm.h:69,
                 from /opt/asus-n53-driver/include/rt_config.h:33,
                 from /opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:28:
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:587:30: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘ULONG {aka long unsigned int}’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/opt/asus-n53-driver/include/os/rt_linux.h:670:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/opt/asus-n53-driver/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro ‘DBGPRINT’
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../common/rt_rf.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../chips/rt30xx.o
/opt/asus-n53-driver/os/linux/../../chips/rt30xx.c: In function ‘RT30xxLoadRFSleepModeSetup’:
/opt/asus-n53-driver/os/linux/../../chips/rt30xx.c:477:9: warning: unused variable ‘MACValue’ [-Wunused-variable]
  UINT32 MACValue;
         ^
/opt/asus-n53-driver/os/linux/../../chips/rt30xx.c: In function ‘RT30xxReverseRFSleepModeSetup’:
/opt/asus-n53-driver/os/linux/../../chips/rt30xx.c:515:9: warning: unused variable ‘MACValue’ [-Wunused-variable]
  UINT32 MACValue;
         ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../chips/rt5592.o
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c:120:26: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR *RF5592Reg_5G = RF5592Reg_5G_Default;
                          ^
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c:179:42: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR_CHANNEL *RF5592Reg_Channel_5G = RF5592Reg_Channel_5G_Default;
                                          ^
In file included from /opt/asus-n53-driver/include/chip/mac_pci.h:33:0,
                 from /opt/asus-n53-driver/include/rtmp_chip.h:37,
                 from /opt/asus-n53-driver/include/rt_config.h:38,
                 from /opt/asus-n53-driver/os/linux/../../chips/rt5592.c:28:
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c: In function ‘RT5592_ChipSwitchChannel’:
/opt/asus-n53-driver/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as ‘true’ for the address of ‘RfReg’ will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/opt/asus-n53-driver/include/chip/rtmp_phy.h:592:2: note: in expansion of macro ‘RF_M_READ8’
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c:1985:4: note: in expansion of macro ‘RF_M_WRITE8’
    RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);
    ^
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c: At top level:
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c:2223:17: warning: initialization discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  .pRFRegTable = RF5592Reg_2G_5G,
                 ^
/opt/asus-n53-driver/os/linux/../../chips/rt5592.c:857:13: warning: ‘RT5592FilterCalibration’ defined but not used [-Wunused-function]
 static VOID RT5592FilterCalibration(IN PRTMP_ADAPTER pAd)
             ^
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /opt/asus-n53-driver/os/linux/../../os/linux/pci_main_dev.o
/opt/asus-n53-driver/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/opt/asus-n53-driver/os/linux/../../os/linux/pci_main_dev.c:334:13: warning: assignment discards ‘const’ qualifier from pointer target type [-Wdiscarded-qualifiers]
  print_name = pci_name(pci_dev);
             ^
/opt/asus-n53-driver/os/linux/../../os/linux/pci_main_dev.c: At top level:
/opt/asus-n53-driver/os/linux/../../os/linux/pci_main_dev.c:481:13: warning: ‘rt2860_remove_one’ defined but not used [-Wunused-function]
 static VOID rt2860_remove_one(
             ^
  LD [M]  /opt/asus-n53-driver/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /opt/asus-n53-driver/os/linux/rt5592sta.o
see include/linux/module.h for more information
  CC      /opt/asus-n53-driver/os/linux/rt5592sta.mod.o
  LD [M]  /opt/asus-n53-driver/os/linux/rt5592sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'
cp -f /opt/asus-n53-driver/os/linux/rt5592sta.ko /tftpboot
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo make install
make -C /opt/asus-n53-driver/os/linux -f Makefile.6 install
make[1]: Entering directory '/opt/asus-n53-driver/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /opt/asus-n53-driver/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.8.0-36-generic
make[1]: Leaving directory '/opt/asus-n53-driver/os/linux'
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo modprobe rt5592sta
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo echo "rt5592sta" > /etc/modules
bash: /etc/modules: Permission denied
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo echo "rt5592sta" > /etc/modules
bash: /etc/modules: Permission denied
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo modprobe rt5592sta
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo echo "rt5592sta" > /etc/modules
bash: /etc/modules: Permission denied
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo make install
make -C /opt/asus-n53-driver/os/linux -f Makefile.6 install
make[1]: Entering directory '/opt/asus-n53-driver/os/linux'
mkdir: cannot create directory ‘/etc/Wireless’: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /opt/asus-n53-driver/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.8.0-36-generic
make[1]: Leaving directory '/opt/asus-n53-driver/os/linux'
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo modprobe rt5592sta
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ sudo echo "rt5592sta" > /etc/modules
bash: /etc/modules: Permission denied
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 
raynskitty@raynskitty-H81M-S2PV:/opt/asus-n53-driver$ 


```

---

### Post by CatKiller on 2017-06-27
Some information on what it is that you're trying to achieve might help.

However, this command won't work: ```
sudo echo "rt5592sta" > /etc/modules
```

Use ```
echo "rt5592sta" | sudo tee -a /etc/modules
``` instead.

---

### Post by 101kitty on 2017-06-27
I'm trying to install my wireless card pce-n53. But I keep getting errors about time and date.

---

### Post by jeremy31 on 2017-06-27
Have you rebooted since trying to install?  What are the results from ```
iwconfig
```

---

### Post by 101kitty on 2017-06-27
```
 enp3s0 no wireless extension

Io no wireless extension 
```

> **jeremy31 said:**
> Have you rebooted since trying to install? 

Yes I've tried rebooting after I installed.

---

### Post by jeremy31 on 2017-06-27
Post results for ```
lspci -nnk
```

---

### Post by 101kitty on 2017-06-27
After a bunch of research i made it this far, ```
 raynskitty@raynskitty-H81M-S2PV:~$ sudo apt-get install build-essential linux-headers-generic git
[sudo] password for raynskitty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
git is already the newest version (1:2.7.4-0ubuntu1.1).
linux-headers-generic is already the newest version (4.4.0.81.87).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raynskitty@raynskitty-H81M-S2PV:~$ cd~
No command 'cd~' found, did you mean:
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdi' from package 'cdo' (universe)
 Command 'cde' from package 'cde' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
cd~: command not found
raynskitty@raynskitty-H81M-S2PV:~$ cd ~
raynskitty@raynskitty-H81M-S2PV:~$ git clone https://github.com/mareksuscak/asus-pce-n53-linux.git
fatal: destination path 'asus-pce-n53-linux' already exists and is not an empty directory.
raynskitty@raynskitty-H81M-S2PV:~$ cd asus-pce-n53-linux
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make
make -C tools
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/tools'
/home/raynskitty/asus-pce-n53-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/raynskitty/asus-pce-n53-linux/os/linux/Makefile
make -C /lib/modules/4.8.0-56-generic/build SUBDIRS=/home/raynskitty/asus-pce-n53-linux/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-56-generic'
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
  LD [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.o
see include/linux/module.h for more information
  LD [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-56-generic'
cp -f /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.ko /tftpboot
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make install
make -C /home/raynskitty/asus-pce-n53-linux/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/raynskitty/asus-pce-n53-linux/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.8.0-56-generic
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo modprobe rt5592sta
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ 




raynskitty@raynskitty-H81M-S2PV:~$ cd ~/asus-pce-n53-linux
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make clean
[sudo] password for raynskitty: 
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../rate_ctrl/*.o
rm -f ../../rate_ctrl/.*.{cmd,flags,d}
rm -f ../../ate/common/*.o
rm -f ../../ate/common/.*.{cmd,flags,d}
rm -f ../../ate/chips/*.o
rm -f ../../ate/chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
rm -rf os/linux/Makefile
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make
make -C tools
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/tools'
/home/raynskitty/asus-pce-n53-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/raynskitty/asus-pce-n53-linux/os/linux/Makefile
make -C /lib/modules/4.8.0-56-generic/build SUBDIRS=/home/raynskitty/asus-pce-n53-linux/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-56-generic'
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_md5.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/include/crypt_aes.h:31,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1459:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1459:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1554:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1554:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:527:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:477:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:528:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:477:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/chip/mac_pci.h:33:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_chip.h:37,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:38,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c: In function &#8216;RTMPAdjustFrequencyOffset&#8217;:
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:583:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;FreqOffset&#8217; will never be NULL [-Waddress]
  if (_pVal1 != NULL)        \
             ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;HighCurrentBit&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_wep.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/action.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_init.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_aes.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_sync.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/eeprom.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_info.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_radar.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/spectrum.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/spectrum.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/spectrum.c:1972:29: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro &#8216;DBGPRINT&#8217;
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rt_channel.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_profile.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_asic.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_T
                            ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_T
                            ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/ps.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/uapsd.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/assoc.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/auth.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sync.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sanity.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/connect.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/wpa.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:29:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:3954:30: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:3954:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rt_os_util.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/ba_action.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../sta/dls.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rt_led.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPFreeTXDUponTxDmaDone&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPHandleMgmtRingDmaDoneInterrupt&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c:735:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/ee_prom.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.o
In file included from ./include/linux/list.h:8:0,
                 from ./include/linux/module.h:9,
                 from /home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:31,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibrationMode&#8217;:
./include/linux/kernel.h:742:17: warning: comparison of distinct pointer types lacks a cast
  (void) (&_min1 == &_min2);  \
                 ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:128:13: note: in expansion of macro &#8216;min&#8217;
   RFValue = min(RFValue, 0x5F);
             ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/chip/mac_pci.h:33:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_chip.h:37,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:38,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:28:
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;RfReg&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:592:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:141:3: note: in expansion of macro &#8216;RF_M_WRITE8&#8217;
   RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);  
   ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/ee_efuse.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o
In file included from /home/raynskitty/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/raynskitty/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../common/rt_rf.o
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt30xx.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xxLoadRFSleepModeSetup&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt30xx.c:477:9: warning: unused variable &#8216;MACValue&#8217; [-Wunused-variable]
  UINT32 MACValue;
         ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xxReverseRFSleepModeSetup&#8217;:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt30xx.c:515:9: warning: unused variable &#8216;MACValue&#8217; [-Wunused-variable]
  UINT32 MACValue;
         ^
  CC [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.o
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:120:26: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR *RF5592Reg_5G = RF5592Reg_5G_Default;
                          ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:179:42: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 REG_PAIR_CHANNEL *RF5592Reg_Channel_5G = RF5592Reg_Channel_5G_Default;
                                          ^
In file included from /home/raynskitty/asus-pce-n53-linux/include/chip/mac_pci.h:33:0,
                 from /home/raynskitty/asus-pce-n53-linux/include/rtmp_chip.h:37,
                 from /home/raynskitty/asus-pce-n53-linux/include/rt_config.h:38,
                 from /home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:28:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c: In function &#8216;RT5592_ChipSwitchChannel&#8217;:
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;RfReg&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/raynskitty/asus-pce-n53-linux/include/chip/rtmp_phy.h:592:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:1985:4: note: in expansion of macro &#8216;RF_M_WRITE8&#8217;
    RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);
    ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c: At top level:
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:2223:17: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
  .pRFRegTable = RF5592Reg_2G_5G,
                 ^
/home/raynskitty/asus-pce-n53-linux/os/linux/../../chips/rt5592.c:857:13: warning: &#8216;RT5592FilterCalibration&#8217; defined but not used [-Wunused-function]
 static VOID RT5592FilterCalibration(IN PRTMP_ADAPTER pAd)
             ^
  LD [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.o
see include/linux/module.h for more information
  LD [M]  /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-56-generic'
cp -f /home/raynskitty/asus-pce-n53-linux/os/linux/rt5592sta.ko /tftpboot
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo make install
make -C /home/raynskitty/asus-pce-n53-linux/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/raynskitty/asus-pce-n53-linux/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.8.0-56-generic
make[1]: Leaving directory '/home/raynskitty/asus-pce-n53-linux/os/linux'
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ sudo modprobe rt5592sta
raynskitty@raynskitty-H81M-S2PV:~/asus-pce-n53-linux$ 



```

and here is the generated out put from ```
lspci -nnk 
```

```
 raynskitty@raynskitty-H81M-S2PV:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd 4th Gen Core Processor DRAM Controller [1458:5000]
    Kernel driver in use: hsw_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1458:d000]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:2010]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB xHCI [1458:5007]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family MEI Controller [1458:1c3a]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI [1458:5006]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset High Definition Audio Controller [1458:a002]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family USB EHCI [1458:5006]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller [8086:8c5c] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd C220 Series Chipset Family H81 Express LPC Controller [1458:5001]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [1458:b005]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: Gigabyte Technology Co., Ltd 8 Series/C220 Series Chipset Family SMBus Controller [1458:5001]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Amethyst XT [Radeon R9 M295X Mac Edition / R9 380X] [1002:6938] (rev f1)
    Subsystem: XFX Pine Group Inc. Tonga XT / Amethyst XT [Radeon R9 380X / R9 M295X Mac Edition] [1682:9385]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380] [1002:aad8]
    Subsystem: XFX Pine Group Inc. Tonga HDMI Audio [Radeon R9 285/380] [1682:aad8]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
    Kernel modules: r8169
04:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
06:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
    Subsystem: ASUSTeK Computer Inc. RT5592 PCIe Wireless Network Adapter [1043:851a]
    Kernel driver in use: rt2860
    Kernel modules: rt5592sta
raynskitty@raynskitty-H81M-S2PV:~$ 

 
```

Referance ```
 https://askubuntu.com/questions/653926/14-04-wifi-ndisgtk-drivers-and-getting-card-working
https://github.com/mareksuscak/asus-pce-n53-linux/issues/4 
```

---

### Post by 101kitty on 2017-06-27
I reinstalled Ubuntu to see if that will fix the problem but it did not.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

y@y-H81M-S2PV:~$ sudo apt-get install build-essential linux-headers-generic git
[sudo] password for y: 
Sorry, try again.
[sudo] password for y: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
The following additional packages will be installed:
  git-man liberror-perl linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-generic
0 upgraded, 6 newly installed, 0 to remove and 208 not upgraded.
Need to get 14.6 MB of archives.
After this operation, 104 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 liberror-perl all 0.17-1.2 [19.6 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git-man all 1:2.7.4-0ubuntu1.1 [735 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git amd64 1:2.7.4-0ubuntu1.1 [3,068 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-81 all 4.4.0-81.104 [9,974 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-81-generic amd64 4.4.0-81.104 [789 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.81.87 [2,280 B]
Fetched 14.6 MB in 1s (13.7 MB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 175313 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.2_all.deb ...
Unpacking liberror-perl (0.17-1.2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.7.4-0ubuntu1.1_all.deb ...
Unpacking git-man (1:2.7.4-0ubuntu1.1) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.7.4-0ubuntu1.1_amd64.deb ...
Unpacking git (1:2.7.4-0ubuntu1.1) ...
Selecting previously unselected package linux-headers-4.4.0-81.
Preparing to unpack .../linux-headers-4.4.0-81_4.4.0-81.104_all.deb ...
Unpacking linux-headers-4.4.0-81 (4.4.0-81.104) ...
Selecting previously unselected package linux-headers-4.4.0-81-generic.
Preparing to unpack .../linux-headers-4.4.0-81-generic_4.4.0-81.104_amd64.deb ...
Unpacking linux-headers-4.4.0-81-generic (4.4.0-81.104) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_4.4.0.81.87_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.81.87) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liberror-perl (0.17-1.2) ...
Setting up git-man (1:2.7.4-0ubuntu1.1) ...
Setting up git (1:2.7.4-0ubuntu1.1) ...
Setting up linux-headers-4.4.0-81 (4.4.0-81.104) ...
Setting up linux-headers-4.4.0-81-generic (4.4.0-81.104) ...
Setting up linux-headers-generic (4.4.0.81.87) ...
y@y-H81M-S2PV:~$ cd ~
y@y-H81M-S2PV:~$ git clone https://github.com/mareksuscak/asus-pce-n53-linux.gitCloning into 'asus-pce-n53-linux'...
remote: Counting objects: 222, done.
remote: Total 222 (delta 0), reused 0 (delta 0), pack-reused 222
Receiving objects: 100% (222/222), 1005.88 KiB | 0 bytes/s, done.
Resolving deltas: 100% (60/60), done.
Checking connectivity... done.
y@y-H81M-S2PV:~$ cd asus-pce-n53-linux
y@y-H81M-S2PV:~/asus-pce-n53-linux$ sudo make
make -C tools
make[1]: Entering directory '/home/y/asus-pce-n53-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/y/asus-pce-n53-linux/tools'
/home/y/asus-pce-n53-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/y/asus-pce-n53-linux/os/linux/Makefile
make -C /lib/modules/4.8.0-36-generic/build SUBDIRS=/home/y/asus-pce-n53-linux/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-36-generic'
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_md5.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.o
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/include/crypt_aes.h:31,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1459:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
                                ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1459:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.
      ^
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1554:32: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
                                ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/crypt_aes.c:1554:6: note: in expansion of macro &#8216;DBGPRINT&#8217;
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failur
      ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/mlme.o
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:527:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:477:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:528:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:477:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 fine NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                         ^
In file included from /home/y/asus-pce-n53-linux/include/chip/mac_pci.h:33:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_chip.h:37,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:38,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c: In function &#8216;RTMPAdjustFrequencyOffset&#8217;:
/home/y/asus-pce-n53-linux/include/chip/rtmp_phy.h:583:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;FreqOffset&#8217; will never be NULL [-Waddress]
  if (_pVal1 != NULL)        \
             ^
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
/home/y/asus-pce-n53-linux/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;HighCurrentBit&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/y/asus-pce-n53-linux/os/linux/../../common/mlme.c:4990:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(pAd, RF_R17, &FreqOffset, &HighCurrentBit, 0x7F);
  ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_wep.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/action.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_init.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_aes.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_sync.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/eeprom.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_info.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.o
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_wpa.c:1031:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_radar.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/spectrum.o
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/spectrum.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/spectrum.c:1972:29: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
                             ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/spectrum.c:1972:3: note: in expansion of macro &#8216;DBGPRINT&#8217;
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffe
   ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rt_channel.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_profile.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_asic.o
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffsetForTemperatureSensor&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c:1178:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry0 = &TxPowerTuningTable[TuningTableIndex0 + TX_POWER_T
                            ^
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_asic.c:1191:28: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
   TxPowerTuningTableEntry1 = &TxPowerTuningTable[TuningTableIndex1 + TX_POWER_T
                            ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/ps.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/uapsd.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_profile.o
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_profile.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_profile.c:411:35: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
                                   ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_profile.c:411:9: note: in expansion of macro &#8216;DBGPRINT&#8217;
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION_
         ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/assoc.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/auth.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/sync.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/sanity.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.o
/home/y/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/y/asus-pce-n53-linux/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/connect.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/wpa.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.o
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:29:
/home/y/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:3954:30: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
                              ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../sta/sta_cfg.c:3954:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), p
    ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rt_os_util.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/ba_action.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../sta/dls.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rt_led.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_mac_pci.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.o
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPFreeTXDUponTxDmaDone&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c:540:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPHandleMgmtRingDmaDoneInterrupt&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/cmm_data_pci.c:735:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function &#8216;RTMPInitPCIeDevice&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../os/linux/rt_rbus_pci_drv.c:1382:23: warning: unused variable &#8216;Index&#8217; [-Wunused-variable]
   UINT32 MacCsr0 = 0, Index= 0;
                       ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/ee_prom.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.o
In file included from ./include/linux/list.h:8:0,
                 from ./include/linux/module.h:9,
                 from /home/y/asus-pce-n53-linux/include/os/rt_linux.h:31,
                 from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibrationMode&#8217;:
./include/linux/kernel.h:742:17: warning: comparison of distinct pointer types lacks a cast
  (void) (&_min1 == &_min2);  \
                 ^
/home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:128:13: note: in expansion of macro &#8216;min&#8217;
   RFValue = min(RFValue, 0x5F);
             ^
In file included from /home/y/asus-pce-n53-linux/include/chip/mac_pci.h:33:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_chip.h:37,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:38,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:28:
/home/y/asus-pce-n53-linux/include/chip/rtmp_phy.h:585:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;RfReg&#8217; will never be NULL [-Waddress]
  if (_pVal2 != NULL)        \
             ^
/home/y/asus-pce-n53-linux/include/chip/rtmp_phy.h:592:2: note: in expansion of macro &#8216;RF_M_READ8&#8217;
  RF_M_READ8(_pAd, _RegId, NULL, &RfReg, _BitMask);  \
  ^
/home/y/asus-pce-n53-linux/os/linux/../../common/frq_cal.c:141:3: note: in expansion of macro &#8216;RF_M_WRITE8&#8217;
   RF_M_WRITE8(pAd, RF_R03, 0x80, 0x80);  
   ^
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/ee_efuse.o
  CC [M]  /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:558:72: error: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/y/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected &#8216;u16 * {aka short unsigned int *}&#8217; but argument is of type &#8216;ULONG * {aka long unsigned int *}&#8217;
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
                              ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:564:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("Write 70f; offset = %x, Configuration = %x. \n", 
    ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:578:72: error: passing argument 3 of &#8216;pci_read_config_word&#8217; from incompatible pointer type [-Werror=incompatible-pointer-types]
 pci_read_config_word(((POS_COOKIE)pAd->OS_Cookie)->pci_dev, offset, &Configurat
                                                                     ^
In file included from /home/y/asus-pce-n53-linux/include/os/rt_linux.h:41:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
./include/linux/pci.h:921:19: note: expected &#8216;u16 * {aka short unsigned int *}&#8217; but argument is of type &#8216;ULONG * {aka long unsigned int *}&#8217;
 static inline int pci_read_config_word(const struct pci_dev *dev, int where, u1
                   ^
In file included from /home/y/asus-pce-n53-linux/include/rtmp_os.h:44:0,
                 from /home/y/asus-pce-n53-linux/include/rtmp_comm.h:69,
                 from /home/y/asus-pce-n53-linux/include/rt_config.h:33,
                 from /home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:28:
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:30: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;ULONG {aka long unsigned int}&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
                              ^
/home/y/asus-pce-n53-linux/include/os/rt_linux.h:670:16: note: in definition of macro &#8216;DBGPRINT_RAW&#8217;
         printk Fmt;               \
                ^
/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.c:587:4: note: in expansion of macro &#8216;DBGPRINT&#8217;
    DBGPRINT(RT_DEBUG_TRACE, ("RadioOnExec restore 70f; offset = %x, Configurati
    ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o' failed
make[2]: *** [/home/y/asus-pce-n53-linux/os/linux/../../common/rtmp_mcu.o] Error 1
Makefile:1491: recipe for target '_module_/home/y/asus-pce-n53-linux/os/linux' failed
make[1]: *** [_module_/home/y/asus-pce-n53-linux/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-36-generic'
Makefile:384: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
y@y-H81M-S2PV:~/asus-pce-n53-linux$ sudo make install
make -C /home/y/asus-pce-n53-linux/os/linux -f Makefile.6 install
make[1]: Entering directory '/home/y/asus-pce-n53-linux/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/y/asus-pce-n53-linux/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/
install: cannot stat 'rt5592sta.ko': No such file or directory
Makefile.6:297: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/y/asus-pce-n53-linux/os/linux'
Makefile:477: recipe for target 'install' failed
make: *** [install] Error 2
y@y-H81M-S2PV:~/asus-pce-n53-linux$ 


```

---

### Post by jeremy31 on 2017-06-27
Post results for ```
modinfo rt2860
```
```
modinfo rt5592sta
```

For some reason it is trying to use rt2860 instead of the rt5592sta you were trying to install.  The rt2860 is not part of the kernel so I have no idea where it came from

[https://github.com/mareksuscak/asus-pce-n53-linux](https://github.com/mareksuscak/asus-pce-n53-linux) will not work at all as it is just patched for the 3.? series kernels.  The other github site [https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10.git](https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10.git) actually built a module

---

### Post by 101kitty on 2017-06-27
So do I need to install 16.10 and follow the directions from that reference.

wait.. i can install 17.10 that should fix the problem right?

---

### Post by jeremy31 on 2017-06-27
I don't know if that source code will compile on 17.10 as there isn't any kernel support for this device at all.

It would be less headaches installing an Intel 7265 without downloading or installing anything

---

### Post by 101kitty on 2017-06-27
That module is for laptops i have a desktop, is there something i can get with 5g support that not to expensive that supports Linux better than my current card?

---

### Post by jeremy31 on 2017-06-27
I would just search for Intel dual band desktop and see what shows up.  Do you need just 5 GHz or actual AC mode?

It may have been the 7260 cards that had a desktop version and the 7260's should work after booting but watch what you are buying as there are some options like dual band(includes 5GHz), AC support, and bluetooth.  I wouldn't bother with bluetooth as depending on the exact bluetooth chipset it might not work

---

### Post by 101kitty on 2017-06-27
i went and purchased a tp-link ac600 installed it using this these commands.
```
 git clone https://github.com/ulli-kroll/mt7610u.git
cd mt7610u
make
sudo make install
sudo cp firmware/*  /lib/firmware
sudo insmod mt7610u.ko 
```

and it not working.


```
a@a-H81M-S2PV:~$ cd mt7610u
a@a-H81M-S2PV:~/mt7610u$ make clean
rm -f */*.o
rm -f */.*.{cmd,flags,d}
rm -f *.{o,ko,mod.{o,c}}
rm -f */*/*.{o,ko,mod.{o,c}}
rm -f */*/.*.{cmd,flags,d}
rm -fr .tmp_versions
rm: cannot remove '.tmp_versions/mt7610u.mod': Permission denied
Makefile:388: recipe for target 'clean' failed
make: *** [clean] Error 1
a@a-H81M-S2PV:~/mt7610u$ sudo make
[sudo] password for a: 
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-22-generic/build M=/home/a/mt7610u modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-22-generic'
  CC [M]  /home/a/mt7610u/sta/assoc.o
  CC [M]  /home/a/mt7610u/sta/auth.o
  CC [M]  /home/a/mt7610u/sta/auth_rsp.o
  CC [M]  /home/a/mt7610u/sta/sync.o
  CC [M]  /home/a/mt7610u/sta/sanity.o
  CC [M]  /home/a/mt7610u/sta/rtmp_data.o
  CC [M]  /home/a/mt7610u/sta/connect.o
  CC [M]  /home/a/mt7610u/sta/wpa.o
  CC [M]  /home/a/mt7610u/sta/sta_cfg.o
/home/a/mt7610u/sta/sta_cfg.c: In function ‘Set_EncrypType_Proc’:
/home/a/mt7610u/sta/sta_cfg.c:401:5: warning: this ‘else’ clause does not guard... [-Wmisleading-indentation]
     else
     ^~~~
/home/a/mt7610u/sta/sta_cfg.c:404:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘else’
  if (pAd->StaCfg.BssType == BSS_ADHOC)
  ^~
/home/a/mt7610u/sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_siwfreq’:
/home/a/mt7610u/sta/sta_cfg.c:1474:5: warning: this ‘else’ clause does not guard... [-Wmisleading-indentation]
     else
     ^~~~
/home/a/mt7610u/sta/sta_cfg.c:1477:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘else’
  return NDIS_STATUS_SUCCESS;
  ^~~~~~
/home/a/mt7610u/sta/sta_cfg.c: In function ‘RtmpIoctl_rt_ioctl_giwrate’:
/home/a/mt7610u/sta/sta_cfg.c:3274:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if (rate_index >= rate_count)
     ^~
/home/a/mt7610u/sta/sta_cfg.c:3277:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
  *(ULONG *)pData = ralinkrate[rate_index] * 500000;
  ^
  CC [M]  /home/a/mt7610u/mgmt/mgmt_vht.o
  CC [M]  /home/a/mt7610u/common/vht.o
  CC [M]  /home/a/mt7610u/common/crypt_md5.o
  CC [M]  /home/a/mt7610u/common/crypt_sha2.o
  CC [M]  /home/a/mt7610u/common/crypt_hmac.o
  CC [M]  /home/a/mt7610u/common/crypt_aes.o
  CC [M]  /home/a/mt7610u/common/crypt_arc4.o
  CC [M]  /home/a/mt7610u/common/mlme.o
  CC [M]  /home/a/mt7610u/common/cmm_wep.o
  CC [M]  /home/a/mt7610u/common/action.o
  CC [M]  /home/a/mt7610u/common/cmm_data.o
  CC [M]  /home/a/mt7610u/common/rtmp_init.o
/home/a/mt7610u/common/rtmp_init.c: In function ‘NICInitializeAsic.part.0’:
/home/a/mt7610u/common/rtmp_init.c:1113:1:  warning: the frame size of 2040 bytes is larger than 1024 bytes  [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/a/mt7610u/common/rtmp_init_inf.o
  CC [M]  /home/a/mt7610u/common/cmm_tkip.o
  CC [M]  /home/a/mt7610u/common/cmm_aes.o
  CC [M]  /home/a/mt7610u/common/cmm_sync.o
/home/a/mt7610u/common/cmm_sync.c: In function ‘BuildChannelList’:
/home/a/mt7610u/common/cmm_sync.c:112:6: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
      if (pChannelList[i] == pAd->TxPower[j].Channel)
      ^~
/home/a/mt7610u/common/cmm_sync.c:114:7:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
       pAd->ChannelList[index + i].Flags = pChannelListFlag[i];
       ^~~
/home/a/mt7610u/common/cmm_sync.c:185:6: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
      if (pChannelList[i] == pAd->TxPower[j].Channel)
      ^~
/home/a/mt7610u/common/cmm_sync.c:187:7:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
       pAd->ChannelList[index + i].Flags = pChannelListFlag[i];
       ^~~
  CC [M]  /home/a/mt7610u/common/cmm_sanity.o
  CC [M]  /home/a/mt7610u/common/cmm_info.o
/home/a/mt7610u/common/cmm_info.c: In function ‘GetEncryptType’:
/home/a/mt7610u/common/cmm_info.c:1201:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if(enc == Ndis802_11Encryption3Enabled)
     ^~
/home/a/mt7610u/common/cmm_info.c:1203:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
  if(enc == Ndis802_11Encryption4Enabled)
  ^~
/home/a/mt7610u/common/cmm_info.c: In function ‘GetAuthMode’:
/home/a/mt7610u/common/cmm_info.c:1213:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if(auth == Ndis802_11AuthModeShared)
     ^~
/home/a/mt7610u/common/cmm_info.c:1215:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
  if(auth == Ndis802_11AuthModeAutoSwitch)
  ^~
/home/a/mt7610u/common/cmm_info.c:1225:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if(auth == Ndis802_11AuthModeWPA2PSK)
     ^~
/home/a/mt7610u/common/cmm_info.c:1227:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
  if(auth == Ndis802_11AuthModeWPA1WPA2)
  ^~
  CC [M]  /home/a/mt7610u/common/cmm_cfg.o
  CC [M]  /home/a/mt7610u/common/cmm_wpa.o
/home/a/mt7610u/common/cmm_wpa.c: In function ‘RTMPToWirelessSta’:
/home/a/mt7610u/common/cmm_wpa.c:387:3: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
   if (pPacket == NULL)
   ^~
/home/a/mt7610u/common/cmm_wpa.c:391:4:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
    if (bClearFrame)
    ^~
/home/a/mt7610u/common/cmm_wpa.c: In function ‘WPAStart2WayGroupHS’:
/home/a/mt7610u/common/cmm_wpa.c:1229:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if ((!pEntry) || !IS_ENTRY_CLIENT(pEntry))
     ^~
/home/a/mt7610u/common/cmm_wpa.c:1234:2:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
  mpool = kmalloc(TX_EAPOL_BUFFER, GFP_ATOMIC);
  ^~~~~
  CC [M]  /home/a/mt7610u/common/cmm_radar.o
  CC [M]  /home/a/mt7610u/common/spectrum.o
  CC [M]  /home/a/mt7610u/common/rtmp_timer.o
  CC [M]  /home/a/mt7610u/common/rt_channel.o
  CC [M]  /home/a/mt7610u/common/cmm_profile.o
  CC [M]  /home/a/mt7610u/common/cmm_asic.o
  CC [M]  /home/a/mt7610u/common/scan.o
  CC [M]  /home/a/mt7610u/common/cmm_cmd.o
  CC [M]  /home/a/mt7610u/common/uapsd.o
  CC [M]  /home/a/mt7610u/common/ps.o
  CC [M]  /home/a/mt7610u/rate_ctrl/ra_ctrl.o
  CC [M]  /home/a/mt7610u/rate_ctrl/alg_legacy.o
  CC [M]  /home/a/mt7610u/rate_ctrl/alg_ags.o
  CC [M]  /home/a/mt7610u/chips/rtmp_chip.o
  CC [M]  /home/a/mt7610u/common/txpower.o
  CC [M]  /home/a/mt7610u/mac/rtmp_mac.o
  CC [M]  /home/a/mt7610u/mgmt/mgmt_entrytb.o
  CC [M]  /home/a/mt7610u/phy/rtmp_phy.o
  CC [M]  /home/a/mt7610u/phy/rlt_phy.o
  CC [M]  /home/a/mt7610u/phy/rlt_rf.o
  CC [M]  /home/a/mt7610u/rate_ctrl/alg_grp.o
/home/a/mt7610u/rate_ctrl/alg_grp.c: In function ‘StaQuickResponeForRateUpExecAdapt’:
/home/a/mt7610u/rate_ctrl/alg_grp.c:1064:38:  warning: comparison of constant ‘2’ with boolean expression is always  false [-Wbool-compare]
   else if (pAd->CommonCfg.TrainUpRule==2 && Rssi<=pAd->CommonCfg.TrainUpRuleRSSI)
                                      ^~
/home/a/mt7610u/rate_ctrl/alg_grp.c:1068:38:  warning: comparison of constant ‘3’ with boolean expression is always  false [-Wbool-compare]
   else if (pAd->CommonCfg.TrainUpRule==3 && Rssi<=pAd->CommonCfg.TrainUpRuleRSSI)
                                      ^~
  CC [M]  /home/a/mt7610u/common/ba_action.o
  CC [M]  /home/a/mt7610u/mgmt/mgmt_ht.o
  CC [M]  /home/a/mt7610u/common/rt_os_util.o
  CC [M]  /home/a/mt7610u/common/rt_led.o
  CC [M]  /home/a/mt7610u/common/cmm_mac_usb.o
/home/a/mt7610u/common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/a/mt7610u/common/cmm_mac_usb.c:257:3: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
   if (pHTTXContext)
   ^~
/home/a/mt7610u/common/cmm_mac_usb.c:264:4:  note: ...this statement, but the latter is misleadingly indented as if  it is guarded by the ‘if’
    if (pCmdRspEventContext->CmdRspBuffer) {
    ^~
  CC [M]  /home/a/mt7610u/common/cmm_data_usb.o
  CC [M]  /home/a/mt7610u/common/rtusb_io.o
  CC [M]  /home/a/mt7610u/common/rtusb_data.o
  CC [M]  /home/a/mt7610u/common/rtusb_bulk.o
  CC [M]  /home/a/mt7610u/common/rt_rf.o
  CC [M]  /home/a/mt7610u/chips/rt65xx.o
  CC [M]  /home/a/mt7610u/chips/mt76x0.o
  CC [M]  /home/a/mt7610u/mac/ral_nmac.o
  CC [M]  /home/a/mt7610u/mcu/mcu.o
  CC [M]  /home/a/mt7610u/mcu/mcu_and.o
  CC [M]  /home/a/mt7610u/common/frq_cal.o
  LD [M]  /home/a/mt7610u/mt7610u.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/a/mt7610u/mt7610u.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-22-generic'
a@a-H81M-S2PV:~/mt7610u$ sudo bash load.sh
bash: load.sh: No such file or directory
a@a-H81M-S2PV:~/mt7610u$ sudo make install
make: *** No rule to make target 'install'.  Stop.
a@a-H81M-S2PV:~/mt7610u$ sudo cp firmware/*  /lib/firmware
a@a-H81M-S2PV:~/mt7610u$ sudo insmod mt7610u.ko
a@a-H81M-S2PV:~/mt7610u$ 


```

---

