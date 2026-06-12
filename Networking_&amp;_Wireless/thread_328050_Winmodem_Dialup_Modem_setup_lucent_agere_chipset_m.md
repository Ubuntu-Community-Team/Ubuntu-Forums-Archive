---
title: "Winmodem Dialup Modem setup lucent agere chipset martian"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2006-12-30
you need to download the full source for martian modem and 2 object files 
an info reference page is here [http://www.physcip.uni-stuttgart.de/heby/ltmodem/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/)

source code though is here. you need this for 2.6 and higher kernels 
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
  martian-full-20061203.tar.gz         03-Dec-2006 17:33  264K
some obeject code:
  ltmdmobj.o-8.31-gcc3.gz              13-Jul-2006 10:59  205K  
  ltmdmobj.o-8.31-gcc4.gz               13-Jul-2006 10:59  211K  

so then extract all files and copy the ltmodemobj files into the directory of martian/ modem folder.

compile script instruction example is here. The goal is to create an executable program called martian_modem

[http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04852.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04852.html)

follow these instructions completely. run make etc... from a terminal window.
(the $ is your prompt for what to type to execute commands from a terminal window)

I extracted these files into my home directory and did it from there and it still worked. You must be in the proper directory where the files are located to run make commands.
After the program is compiled and is installed with modprobe and you get confirmation that it is properly installed (read and follow the script), you must run this new program before setting up dialup connection. Running martian_modem gives you the port number of the modem. just type martian_modem from terminal window.
Now goto system - administration - networking 
click New  - modem connection
type in phone number, login, password etc....
click hardware, then click the modem you created to set the port ID you get from running martian_modem. You can type or copy this into the port field. set baud flow control etc....
after you have it set up, go back to Devices tab and click the green activate button and it should dial out and connect.

After you get this all working, you can put the martian_modem exectuble into the start up init 6 so it runs whenever you boot linux. Otherwise, you will have to run this from a terminal window before dialing out.

I did this using fedora core 6 and I bet ubuntu is very much the same process.

---

### Post by sdowney717 on 2006-12-30
I am posting this from fedora  core 6 right now using a lucent agere chipset win modem.
I am very new to linux and if I did this, you can also do it.

---

### Post by sdowney717 on 2006-12-30
here is the script in case somehow that site goes down.

This is just to provide an example of a successful build and compile.

The package is expanded with:
$ tar jxf martian-20061203.tar.bz2
Move in with:
$ cd martain
Look around:

$ ls
ChangeLog  INSTALL  Makefile   modem   scripts
Concept    kmodule  martian.h  README

The martian-20061203.tar.bz2 does not contain the precompiled
ltmdmobj.o proprietary component of AgereSystems 8.30.  It must be
taken from the modem/ folder of one of the earlier full releases, and
copied into the modem/ subfolder
$ cp FromSomewhere/ltmdmobj.o  modem/

Then do the usual precautionary:
$ make clean
make -C kmodule/ clean
make[1]: Entering directory `/usr/src/modules/martian-20061203/kmodule'
make -C /lib/modules/2.6.17/build
M="/usr/src/modules/martian-20061203/kmodule" clean
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
make[1]: Leaving directory `/usr/src/modules/martian-20061203/kmodule'
make -C modem/ clean
make[1]: Entering directory `/usr/src/modules/martian-20061203/modem'
-e     RM       OBJS
-e     RM       BINS
-e     RM       TOOLS
make[1]: Leaving directory `/usr/src/modules/martian-20061203/modem'

Currently I'm using a custom 2.6.17 kernel+modules built with a Ubuntu
/usr/src/linux-source-2.6.17  . The compile is started with:
$ make
make -C kmodule/ modules
make[1]: Entering directory `/usr/src/modules/martian-20061203/kmodule'
make -C /lib/modules/2.6.17/build
M="/usr/src/modules/martian-20061203/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
 CC [M]  /usr/src/modules/martian-20061203/kmodule/martian.o
/usr/src/modules/martian-20061203/kmodule/martian.c: In function 'martian_isr':
/usr/src/modules/martian-20061203/kmodule/martian.c:160: warning:
value computed is not used
 CC [M]  /usr/src/modules/martian-20061203/kmodule/marsio.o
 CC [M]  /usr/src/modules/martian-20061203/kmodule/mfifo.o
 LD [M]  /usr/src/modules/martian-20061203/kmodule/martian_dev.o
 Building modules, stage 2.
 MODPOST
 CC      /usr/src/modules/martian-20061203/kmodule/martian_dev.mod.o
 LD [M]  /usr/src/modules/martian-20061203/kmodule/martian_dev.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
make[1]: Leaving directory `/usr/src/modules/martian-20061203/kmodule'
make -C modem/ all
make[1]: Entering directory `/usr/src/modules/martian-20061203/modem'
-e     CC       main.o
-e     CC       dumpers.o
-e     CC       log.o
-e     CC       session.o
-e     CC       mport.o
-e     CC       pty.o
-e     CC       sysdep.o
-e     CC       isr.o
-e     CC       smp.o
-e     CC       core_if.o
-e     CC       coresubst.o
-e     CC       link.o
-e     CC       tweakrelocsdynamic.o
-e     CC       coreadd.o
-e     CC       elf386tweakrelocs
-e     LD       marscore.o
-e     TWEAK    marscore.o
-e     LD       martian_modem
make[1]: Leaving directory `/usr/src/modules/martian-20061203/modem'

With desired products:
$ ls -l kmodule/*.ko
-rw-r--r-- 1 marv marv 26146 2006-12-03 01:34 kmodule/martian_dev.ko
and
$ ls -l  modem/martian*
-rwxr-xr-x 1 marv marv 648428 2006-12-03 01:34 modem/martian_modem

To do the install, most Users will first do
$ su  - root
while Ubuntu related distros will use the alternate sudo:

$ sudo make install
Password:
make -C kmodule/ install
make[1]: Entering directory `/usr/src/modules/martian-20061203/kmodule'
make -C /lib/modules/2.6.17/build
M="/usr/src/modules/martian-20061203/kmodule" modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
 INSTALL /usr/src/modules/martian-20061203/kmodule/martian_dev.ko
 DEPMOD  2.6.17.13-marv1
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
if ! /sbin/modprobe -nq martian_dev ; then /sbin/depmod -a; fi
make[1]: Leaving directory `/usr/src/modules/martian-20061203/kmodule'
make -C modem/ install
make[1]: Entering directory `/usr/src/modules/martian-20061203/modem'
-e     LD       martian_modem.debug
-e     STRIP    martian_modem.debug
-e     STRIP    martian_modem.stripped
-e     INSTALL  /usr/sbin/martian_modem
-e     INSTALL  /usr/lib/debug/usr/sbin/martian_modem.debug
make[1]: Leaving directory `/usr/src/modules/martian-20061203/modem'

Note that because of a non-standard nomenclature in my kernel-source,
the martian_drv was misintalled to:
$ tree /lib/modules/2.6.17.13-marv1
/lib/modules/2.6.17.13-marv1
|-- extra
|   `-- martian_dev.ko

While my kernel is:
$ uname -r
2.6.17

More broadly, the driver could be found with:
$  find  /lib/modules  -name martian?
and this check is worth doing as the install is also mis-directed
under Mandiva/Mandrake and perhaps some other Linux distros

So to correct, make a target folder:
$ sudo mkdir /lib/modules/2.6.17/extra
Copy the driver over:
$ sudo cp /lib/modules/2.6.17.13-marv1/extra/*.ko   /lib/modules/2.6.17/extra/
and verify it go there:
$ ls  /lib/modules/2.6.17/extra/
martian_dev.ko

Have the System check the dependencies:
$ sudo depmod -a
which reported no problems.

The driver is installed with:
$ sudo modprobe martian_dev
$ lsmod | grep martian
martian_dev            18260  0
confirms the loading into the kernel

The helper utility was properly installed to:
$ ls /usr/sbin/martian*
/usr/sbin/martian_modem

Calling the helper application
$ sudo martian_modem
martian: error: open: No such file or directory
martian: info: Mars DSP164x device is not detected
------
This failure report was appropriate, as this laptop has a different
modem hardware.

More later from a different PC

MarvS

---

### Post by eduac on 2007-07-20
Fellas,

I got these errors messages:

> 
root@eduardo-desktop:/usr/src/modules/martian-20061203# make all 
make -C kmodule/ modules 
make[1]: Entering directory `/usr/src/modules/martian-20061203/kmodule' 
make -C /lib/modules/2.6.20-15-generic/build M="/usr/src/modules/martian-20061203/kmodule"  modules 
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
make[1]: Leaving directory `/usr/src/modules/martian-20061203/kmodule' 
make -C modem/ all 
make[1]: Entering directory `/usr/src/modules/martian-20061203/modem' 
-e     CC       main.o 
main.c:15:19: error: stdio.h: No such file or directory 
main.c:17:40: error: sys/mman.h: No such file or directory 
main.c:18:36: error: string.h: No such file or directory 
main.c:19:23: error: asm/types.h: No such file or directory 
In file included from main.c:20: 
mixspinlock.h:9: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘lock’ 
mixspinlock.h: In function ‘mspin_lock’: 
mixspinlock.h:24: error: ‘mspinlock_t’ has no member named ‘lock’ 
mixspinlock.h:13: error: invalid lvalue in asm output 0 
mixspinlock.h: In function ‘mspin_unlock’: 
mixspinlock.h:31: error: ‘mspinlock_t’ has no member named ‘lock’ 
mixspinlock.h:29: error: invalid lvalue in asm output 0 
In file included from main.c:21: 
../martian.h: At top level: 
../martian.h:39: error: expected specifier-qualifier-list before ‘__u16’ 
../martian.h:89: error: expected specifier-qualifier-list before ‘__u16’ 
main.c:23:43: error: signal.h: No such file or directory 
main.c:25:30: error: unistd.h: No such file or directory 
main.c:26:29: error: stdlib.h: No such file or directory 
main.c:28:23: error: sys/types.h: No such file or directory 
main.c:30:36: error: ctype.h: No such file or directory 
main.c:33:42: error: sched.h: No such file or directory 
main.c:35:38: error: stdint.h: No such file or directory 
main.c:37:39: error: pwd.h: No such file or directory 
main.c:38:17: error: grp.h: No such file or directory 
main.c:39:22: error: sys/stat.h: No such file or directory 
main.c:42:20: error: getopt.h: No such file or directory 
main.c:43:45: error: sys/ioctl.h: No such file or directory 
In file included from main.c:45: 
sysdep.h:4:18: error: time.h: No such file or directory 
In file included from main.c:45: 
sysdep.h:6: error: expected specifier-qualifier-list before ‘timer_t’ 
sysdep.h:10: error: expected ‘)’ before ‘clock’ 
In file included from log.h:7, 
                 from main.c:50: 
common.h:31: error: expected specifier-qualifier-list before ‘uid_t’ 
main.c: In function ‘check_procfs’: 
main.c:76: warning: implicit declaration of function ‘system’ 
main.c: In function ‘watch_setup’: 
main.c:82: error: ‘struct _config’ has no member named ‘haveTSC’ 
main.c:85: error: ‘NULL’ undeclared (first use in this function) 
main.c:85: error: (Each undeclared identifier is reported only once 
main.c:85: error: for each function it appears in.) 
main.c:92: error: ‘FILE’ undeclared (first use in this function) 
main.c:92: error: ‘fp’ undeclared (first use in this function) 
main.c:92: warning: implicit declaration of function ‘popen’ 
main.c:97: warning: implicit declaration of function ‘fgetc’ 
main.c:97: error: ‘EOF’ undeclared (first use in this function) 
main.c:98: warning: implicit declaration of function ‘isdigit’ 
main.c:99: warning: implicit declaration of function ‘ungetc’ 
main.c:103: warning: implicit declaration of function ‘fscanf’ 
main.c:103: warning: incompatible implicit declaration of built-in function ‘fscanf’ 
main.c:105: warning: implicit declaration of function ‘pclose’ 
main.c:110: error: ‘struct _config’ has no member named ‘haveTSC’ 
main.c: In function ‘realtime_setup’: 
main.c:120: warning: implicit declaration of function ‘mlockall’ 
main.c:120: error: ‘MCL_CURRENT’ undeclared (first use in this function) 
main.c:121: error: ‘NULL’ undeclared (first use in this function) 
main.c:125: error: storage size of ‘p’ isn’t known 
main.c:126: warning: implicit declaration of function ‘sched_get_priority_min’ 
main.c:126: error: ‘SCHED_FIFO’ undeclared (first use in this function) 
main.c:132: warning: implicit declaration of function ‘sched_setscheduler’ 
main.c:138: warning: implicit declaration of function ‘sched_getparam’ 
main.c:139: warning: implicit declaration of function ‘sched_getscheduler’ 
main.c:125: warning: unused variable ‘p’ 
main.c: In function ‘usage’: 
main.c:148: warning: implicit declaration of function ‘fprintf’ 
main.c:148: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:148: error: ‘stdout’ undeclared (first use in this function) 
main.c:171: warning: implicit declaration of function ‘exit’ 
main.c:171: warning: incompatible implicit declaration of built-in function ‘exit’ 
main.c: In function ‘fix_id_to_code’: 
main.c:176: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OldCountryIdToCountryCode’ 
main.c:176: error: ‘OldCountryIdToCountryCode’ undeclared (first use in this function) 
main.c:178: error: expected specifier-qualifier-list before ‘__u16’ 
main.c:181: warning: excess elements in struct initializer 
main.c:181: warning: (near initialization for ‘IdtoCodeFix[0]’) 
main.c:181: warning: excess elements in struct initializer 
main.c:181: warning: (near initialization for ‘IdtoCodeFix[0]’) 
main.c:182: warning: excess elements in struct initializer 
main.c:182: warning: (near initialization for ‘IdtoCodeFix[1]’) 
main.c:182: warning: excess elements in struct initializer 
main.c:182: warning: (near initialization for ‘IdtoCodeFix[1]’) 
main.c:183: warning: excess elements in struct initializer 
main.c:183: warning: (near initialization for ‘IdtoCodeFix[2]’) 
main.c:183: warning: excess elements in struct initializer 
main.c:183: warning: (near initialization for ‘IdtoCodeFix[2]’) 
main.c:184: warning: excess elements in struct initializer 
main.c:184: warning: (near initialization for ‘IdtoCodeFix[3]’) 
main.c:184: warning: excess elements in struct initializer 
main.c:184: warning: (near initialization for ‘IdtoCodeFix[3]’) 
main.c:185: warning: excess elements in struct initializer 
main.c:185: warning: (near initialization for ‘IdtoCodeFix[4]’) 
main.c:185: warning: excess elements in struct initializer 
main.c:185: warning: (near initialization for ‘IdtoCodeFix[4]’) 
main.c:186: warning: excess elements in struct initializer 
main.c:186: warning: (near initialization for ‘IdtoCodeFix[5]’) 
main.c:186: warning: excess elements in struct initializer 
main.c:186: warning: (near initialization for ‘IdtoCodeFix[5]’) 
main.c:187: warning: excess elements in struct initializer 
main.c:187: warning: (near initialization for ‘IdtoCodeFix[6]’) 
main.c:187: warning: excess elements in struct initializer 
main.c:187: warning: (near initialization for ‘IdtoCodeFix[6]’) 
main.c:188: warning: excess elements in struct initializer 
main.c:188: warning: (near initialization for ‘IdtoCodeFix[7]’) 
main.c:188: warning: excess elements in struct initializer 
main.c:188: warning: (near initialization for ‘IdtoCodeFix[7]’) 
main.c:189: warning: excess elements in struct initializer 
main.c:189: warning: (near initialization for ‘IdtoCodeFix[8]’) 
main.c:189: warning: excess elements in struct initializer 
main.c:189: warning: (near initialization for ‘IdtoCodeFix[8]’) 
main.c:190: warning: excess elements in struct initializer 
main.c:190: warning: (near initialization for ‘IdtoCodeFix[9]’) 
main.c:190: warning: excess elements in struct initializer 
main.c:190: warning: (near initialization for ‘IdtoCodeFix[9]’) 
main.c:194: warning: division by zero 
main.c:195: error: ‘struct <anonymous>’ has no member named ‘id’ 
main.c:195: error: ‘struct <anonymous>’ has no member named ‘code’ 
main.c: At top level: 
main.c:301: error: ‘NULL’ undeclared here (not in a function) 
main.c: In function ‘mcountry_match’: 
main.c:306: warning: implicit declaration of function ‘strchr’ 
main.c:306: warning: incompatible implicit declaration of built-in function ‘strchr’ 
main.c:309: warning: implicit declaration of function ‘strncasecmp’ 
main.c:312: warning: implicit declaration of function ‘strcasecmp’ 
main.c: In function ‘parse_arguments’: 
main.c:330: error: array type has incomplete element type 
main.c:331: error: ‘required_argument’ undeclared (first use in this function) 
main.c:332: error: ‘no_argument’ undeclared (first use in this function) 
main.c:353: error: ‘struct _config’ has no member named ‘realtime’ 
main.c:353: warning: statement with no effect 
main.c:354: error: ‘struct _config’ has no member named ‘syslog’ 
main.c:354: warning: statement with no effect 
main.c:355: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:355: warning: statement with no effect 
main.c:356: error: ‘struct _config’ has no member named ‘logfile’ 
main.c:356: warning: statement with no effect 
main.c:357: error: ‘struct _config’ has no member named ‘check_carrier’ 
main.c:357: warning: statement with no effect 
main.c:359: error: ‘struct _config’ has no member named ‘misr’ 
main.c:359: warning: statement with no effect 
main.c:360: error: ‘struct _config’ has no member named ‘hide_pty’ 
main.c:360: warning: statement with no effect 
main.c:361: error: ‘struct _config’ has no member named ‘true_smp’ 
main.c:361: warning: statement with no effect 
main.c:362: error: ‘struct _config’ has no member named ‘move_fifos’ 
main.c:362: warning: statement with no effect 
main.c:364: error: ‘struct _config’ has no member named ‘permissions’ 
main.c:364: warning: statement with no effect 
main.c:365: error: ‘struct _config’ has no member named ‘mode’ 
main.c:365: warning: statement with no effect 
main.c:367: error: ‘struct _config’ has no member named ‘uid’ 
main.c:367: warning: statement with no effect 
main.c:368: error: ‘struct _config’ has no member named ‘gid’ 
main.c:368: warning: statement with no effect 
main.c:372: error: ‘opterr’ undeclared (first use in this function) 
main.c:372: warning: statement with no effect 
main.c:375: warning: implicit declaration of function ‘getopt_long’ 
main.c:379: error: ‘struct _config’ has no member named ‘realtime’ 
main.c:379: warning: statement with no effect 
main.c:384: warning: implicit declaration of function ‘strcmp’ 
main.c:384: error: ‘optarg’ undeclared (first use in this function) 
main.c:385: error: ‘struct _config’ has no member named ‘misr’ 
main.c:385: warning: statement with no effect 
main.c:388: error: ‘struct _config’ has no member named ‘misr’ 
main.c:388: warning: statement with no effect 
main.c:391: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:392: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:392: error: ‘stderr’ undeclared (first use in this function) 
main.c:392: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:398: error: ‘struct _config’ has no member named ‘syslog’ 
main.c:399: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:402: error: ‘struct _config’ has no member named ‘logfile’ 
main.c:402: warning: statement with no effect 
main.c:403: warning: passing argument 1 of ‘log_redirect_to_file’ from incompatible pointer type 
main.c:406: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:410: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:416: warning: assignment from incompatible pointer type 
main.c:420: warning: implicit declaration of function ‘atoi’ 
main.c:422: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:428: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:428: warning: statement with no effect 
main.c:434: error: ‘struct _config’ has no member named ‘logfile’ 
main.c:435: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:438: error: ‘struct _config’ has no member named ‘syslog’ 
main.c:438: warning: statement with no effect 
main.c:447: error: ‘struct _config’ has no member named ‘check_carrier’ 
main.c:447: warning: statement with no effect 
main.c:451: error: ‘struct _config’ has no member named ‘hide_pty’ 
main.c:451: warning: statement with no effect 
main.c:455: error: ‘struct _config’ has no member named ‘true_smp’ 
main.c:455: warning: statement with no effect 
main.c:459: error: ‘struct _config’ has no member named ‘move_fifos’ 
main.c:459: warning: statement with no effect 
main.c:464: warning: implicit declaration of function ‘getpwnam’ 
main.c:464: warning: initialization makes pointer from integer without a cast 
main.c:467: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:469: error: ‘struct _config’ has no member named ‘uid’ 
main.c:469: error: dereferencing pointer to incomplete type 
main.c:469: error: request for member ‘pw_uid’ in something not a structure or union 
main.c:469: warning: statement with no effect 
main.c:476: warning: implicit declaration of function ‘getgrnam’ 
main.c:476: warning: initialization makes pointer from integer without a cast 
main.c:479: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:481: error: ‘struct _config’ has no member named ‘gid’ 
main.c:481: error: dereferencing pointer to incomplete type 
main.c:481: error: request for member ‘gr_gid’ in something not a structure or union 
main.c:481: warning: statement with no effect 
main.c:487: error: ‘struct _config’ has no member named ‘mode’ 
main.c:487: warning: implicit declaration of function ‘strtol’ 
main.c:487: warning: statement with no effect 
main.c:488: error: ‘struct _config’ has no member named ‘mode’ 
main.c:488: error: ‘S_IRWXU’ undeclared (first use in this function) 
main.c:488: error: ‘S_IRWXG’ undeclared (first use in this function) 
main.c:488: error: invalid operands to binary | 
main.c:488: error: ‘S_IRWXO’ undeclared (first use in this function) 
main.c:488: error: invalid operands to binary | 
main.c:488: error: wrong type argument to bit-complement 
main.c:488: error: invalid operands to binary & 
main.c:489: error: ‘struct _config’ has no member named ‘mode’ 
main.c:489: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:490: error: ‘struct _config’ has no member named ‘permissions’ 
main.c:490: warning: statement with no effect 
main.c:493: error: ‘struct _config’ has no member named ‘permissions’ 
main.c:493: warning: statement with no effect 
main.c:501: warning: passing argument 1 of ‘mcountry_match’ from incompatible pointer type 
main.c:503: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OldCountryIdToCountryCode’ 
main.c:503: error: ‘OldCountryIdToCountryCode’ undeclared (first use in this function) 
main.c:503: warning: statement with no effect 
main.c:507: error: invalid operands to binary == 
main.c:508: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:509: error: ‘struct _config’ has no member named ‘country_id’ 
main.c:509: warning: statement with no effect 
main.c:514: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:515: error: ‘struct _config’ has no member named ‘country_id’ 
main.c:515: warning: statement with no effect 
main.c:523: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:524: error: ‘struct _config’ has no member named ‘country_id’ 
main.c:524: warning: statement with no effect 
main.c:530: warning: pointer type mismatch in conditional expression 
main.c:530: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:533: warning: implicit declaration of function ‘printf’ 
main.c:533: warning: incompatible implicit declaration of built-in function ‘printf’ 
main.c:538: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:541: warning: incompatible implicit declaration of built-in function ‘exit’ 
main.c:544: error: ‘optind’ undeclared (first use in this function) 
main.c:544: warning: comparison between pointer and integer 
main.c:545: error: array subscript is not an integer 
main.c:545: warning: assignment from incompatible pointer type 
main.c:547: warning: comparison between pointer and integer 
main.c:548: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:554: warning: comparison between pointer and integer 
main.c:554: warning: comparison between pointer and integer 
main.c:556: error: ‘optopt’ undeclared (first use in this function) 
main.c:557: warning: comparison between pointer and integer 
main.c:557: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast 
main.c:557: error: ‘struct <anonymous>’ has no member named ‘has_arg’ 
main.c:558: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:558: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast 
main.c:558: error: ‘struct <anonymous>’ has no member named ‘name’ 
main.c:558: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:558: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’ 
main.c:565: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:566: warning: comparison between pointer and integer 
main.c:566: warning: comparison between pointer and integer 
main.c:569: warning: comparison between pointer and integer 
main.c:569: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast 
main.c:569: error: ‘struct <anonymous>’ has no member named ‘has_arg’ 
main.c:570: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:570: warning: passing argument 1 of ‘optslot’ makes integer from pointer without a cast 
main.c:570: error: ‘struct <anonymous>’ has no member named ‘name’ 
main.c:570: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:570: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’ 
main.c:572: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:572: warning: format ‘%c’ expects type ‘int’, but argument 4 has type ‘const struct <anonymous> *’ 
main.c:574: warning: implicit declaration of function ‘strncmp’ 
main.c:574: error: array subscript is not an integer 
main.c:575: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:575: error: array subscript is not an integer 
main.c:575: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:575: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’ 
main.c:578: warning: incompatible implicit declaration of built-in function ‘fprintf’ 
main.c:578: error: array subscript is not an integer 
main.c:578: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:578: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘const struct <anonymous> *’ 
main.c:579: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type 
main.c:330: warning: unused variable ‘options’ 
main.c: In function ‘setup_pin_timer’: 
main.c:601: error: storage size of ‘ptyevent’ isn’t known 
main.c:605: warning: implicit declaration of function ‘memset’ 
main.c:605: warning: incompatible implicit declaration of built-in function ‘memset’ 
main.c:605: warning: passing argument 3 of ‘memset’ makes integer from pointer without a cast 
main.c:608: error: request for member ‘sigev_signo’ in something not a structure or union 
main.c:608: error: ‘SIGRTMIN’ undeclared (first use in this function) 
main.c:608: warning: statement with no effect 
main.c:611: error: request for member ‘sigev_notify’ in something not a structure or union 
main.c:611: error: ‘SIGEV_THREAD_ID’ undeclared (first use in this function) 
main.c:611: warning: statement with no effect 
main.c:612: error: request for member ‘_sigev_un’ in something not a structure or union 
main.c:612: error: request for member ‘_tid’ in something not a structure or union 
main.c:612: warning: statement with no effect 
main.c:614: warning: implicit declaration of function ‘mtimer_create’ 
main.c:614: error: ‘CLOCK_REALTIME’ undeclared (first use in this function) 
main.c:616: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:621: error: ‘mtimer_t’ has no member named ‘id’ 
main.c:621: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:622: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:625: warning: passing argument 3 of ‘memset’ makes integer from pointer without a cast 
main.c:628: error: request for member ‘sigev_signo’ in something not a structure or union 
main.c:628: warning: statement with no effect 
main.c:629: error: request for member ‘sigev_notify’ in something not a structure or union 
main.c:629: error: ‘SIGEV_SIGNAL’ undeclared (first use in this function) 
main.c:629: warning: statement with no effect 
main.c:636: error: ‘mtimer_t’ has no member named ‘id’ 
main.c:636: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:640: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:601: warning: unused variable ‘ptyevent’ 
main.c: At top level: 
main.c:645: error: expected specifier-qualifier-list before ‘uint8_t’ 
main.c:658: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘io_uart_msr’ 
main.c:659: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘io_uart_status’ 
main.c:663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dp_dsp_status’ 
main.c:664: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dp_wDspRetrainState’ 
main.c: In function ‘monitor_state’: 
main.c:717: error: ‘io_uart_msr’ undeclared (first use in this function) 
main.c:717: error: ‘struct _state’ has no member named ‘io_uart_msr’ 
main.c:717: warning: implicit declaration of function ‘sprintf’ 
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:717: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:717: warning: implicit declaration of function ‘__STRING’ 
main.c:717: error: expected ‘)’ before string constant 
main.c:717: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:717: error: ‘struct _state’ has no member named ‘io_uart_msr’ 
main.c:717: warning: statement with no effect 
main.c:718: error: ‘io_uart_status’ undeclared (first use in this function) 
main.c:718: error: ‘struct _state’ has no member named ‘io_uart_status’ 
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:718: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:718: error: expected ‘)’ before string constant 
main.c:718: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:718: error: ‘struct _state’ has no member named ‘io_uart_status’ 
main.c:718: warning: statement with no effect 
main.c:719: error: ‘struct _state’ has no member named ‘x_modem_state’ 
main.c:719: warning: comparison between pointer and integer 
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:719: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:719: error: expected ‘)’ before string constant 
main.c:719: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:719: error: ‘struct _state’ has no member named ‘x_modem_state’ 
main.c:719: warning: statement with no effect 
main.c:720: error: ‘struct _state’ has no member named ‘x_modem_mode’ 
main.c:720: warning: comparison between pointer and integer 
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:720: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:720: error: expected ‘)’ before string constant 
main.c:720: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:720: error: ‘struct _state’ has no member named ‘x_modem_mode’ 
main.c:720: warning: statement with no effect 
main.c:721: error: ‘struct _state’ has no member named ‘x_line_rate’ 
main.c:721: warning: comparison between pointer and integer 
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:721: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:721: error: expected ‘)’ before string constant 
main.c:721: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:721: error: ‘struct _state’ has no member named ‘x_line_rate’ 
main.c:721: warning: statement with no effect 
main.c:722: error: ‘dp_dsp_status’ undeclared (first use in this function) 
main.c:722: error: ‘struct _state’ has no member named ‘dp_dsp_status’ 
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:722: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:722: error: expected ‘)’ before string constant 
main.c:722: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:722: error: ‘struct _state’ has no member named ‘dp_dsp_status’ 
main.c:722: warning: statement with no effect 
main.c:723: error: ‘struct _state’ has no member named ‘io_app_tx_count’ 
main.c:723: warning: comparison between pointer and integer 
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:723: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:723: error: expected ‘)’ before string constant 
main.c:723: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:723: error: ‘struct _state’ has no member named ‘io_app_tx_count’ 
main.c:723: warning: statement with no effect 
main.c:725: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:726: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:730: error: ‘struct _state’ has no member named ‘io_app_tx_bytes’ 
main.c:730: warning: comparison between pointer and integer 
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:730: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:730: error: ‘io_app_tx’ undeclared (first use in this function) 
main.c:730: error: expected ‘)’ before string constant 
main.c:730: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:730: error: ‘struct _state’ has no member named ‘io_app_tx_bytes’ 
main.c:730: warning: statement with no effect 
main.c:731: error: ‘struct _state’ has no member named ‘io_dte_tx_bytes’ 
main.c:731: warning: comparison between pointer and integer 
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:731: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:731: error: ‘io_dte_tx’ undeclared (first use in this function) 
main.c:731: error: expected ‘)’ before string constant 
main.c:731: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:731: error: ‘struct _state’ has no member named ‘io_dte_tx_bytes’ 
main.c:731: warning: statement with no effect 
main.c:732: error: ‘struct _state’ has no member named ‘io_dte_rx_bytes’ 
main.c:732: warning: comparison between pointer and integer 
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:732: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:732: error: ‘io_dte_rx’ undeclared (first use in this function) 
main.c:732: error: expected ‘)’ before string constant 
main.c:732: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:732: error: ‘struct _state’ has no member named ‘io_dte_rx_bytes’ 
main.c:732: warning: statement with no effect 
main.c:733: error: ‘struct _state’ has no member named ‘io_dce_tx_bytes’ 
main.c:733: warning: comparison between pointer and integer 
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:733: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:733: error: ‘io_dce_tx’ undeclared (first use in this function) 
main.c:733: error: expected ‘)’ before string constant 
main.c:733: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:733: error: ‘struct _state’ has no member named ‘io_dce_tx_bytes’ 
main.c:733: warning: statement with no effect 
main.c:734: error: ‘struct _state’ has no member named ‘io_dce_rx_bytes’ 
main.c:734: warning: comparison between pointer and integer 
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:734: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:734: error: ‘io_dce_rx’ undeclared (first use in this function) 
main.c:734: error: expected ‘)’ before string constant 
main.c:734: warning: passing argument 2 of ‘sprintf’ makes pointer from integer without a cast 
main.c:734: error: ‘struct _state’ has no member named ‘io_dce_rx_bytes’ 
main.c:734: warning: statement with no effect 
main.c:736: warning: incompatible implicit declaration of built-in function ‘sprintf’ 
main.c:737: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c: In function ‘setup_pin_watcher’: 
main.c:758: error: storage size of ‘timer_action’ isn’t known 
main.c:760: error: request for member ‘sa_handler’ in something not a structure or union 
main.c:760: warning: statement with no effect 
main.c:761: error: request for member ‘sa_flags’ in something not a structure or union 
main.c:761: warning: statement with no effect 
main.c:762: warning: implicit declaration of function ‘sigemptyset’ 
main.c:762: error: request for member ‘sa_mask’ in something not a structure or union 
main.c:763: warning: implicit declaration of function ‘sigaction’ 
main.c:763: error: ‘SIGRTMIN’ undeclared (first use in this function) 
main.c:758: warning: unused variable ‘timer_action’ 
main.c:766:19: error: errno.h: No such file or directory 
main.c: At top level: 
main.c:769: error: expected ‘)’ before ‘*’ token 
main.c: In function ‘main’: 
main.c:837: error: ‘struct _config’ has no member named ‘syslog’ 
main.c:840: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:841: warning: implicit declaration of function ‘daemon’ 
main.c:841: error: ‘struct _config’ has no member named ‘logfile’ 
main.c:843: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:844: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:845: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:845: warning: statement with no effect 
main.c:848: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:848: error: ‘struct _config’ has no member named ‘logfile’ 
main.c:849: error: ‘struct _config’ has no member named ‘syslog’ 
main.c:849: warning: statement with no effect 
main.c:852: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:862: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:871: warning: implicit declaration of function ‘snprintf’ 
main.c:871: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
main.c:874: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
main.c:878: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
main.c:880: warning: implicit declaration of function ‘strlen’ 
main.c:880: warning: incompatible implicit declaration of built-in function ‘strlen’ 
main.c:885: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:888: error: ‘struct _config’ has no member named ‘misr’ 
main.c:888: error: incompatible type for argument 1 of ‘misr_str’ 
main.c:888: error: ‘struct _config’ has no member named ‘realtime’ 
main.c:888: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:909: warning: passing argument 2 of ‘mthread_create’ discards qualifiers from pointer target type 
main.c:910: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:913: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:924: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:928: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:933: warning: implicit declaration of function ‘mkfifo’ 
main.c:934: error: ‘errno’ undeclared (first use in this function) 
main.c:934: error: ‘EEXIST’ undeclared (first use in this function) 
main.c:935: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:937: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:940: error: ‘FILE’ undeclared (first use in this function) 
main.c:940: error: ‘control’ undeclared (first use in this function) 
main.c:940: error: invalid operands to binary * 
main.c:940: warning: statement with no effect 
main.c:943: warning: implicit declaration of function ‘fopen’ 
main.c:943: warning: statement with no effect 
main.c:944: error: ‘EINTR’ undeclared (first use in this function) 
main.c:950: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:951: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:958: warning: implicit declaration of function ‘get_cmd’ 
main.c:961: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:962: warning: implicit declaration of function ‘fclose’ 
main.c:964: warning: statement with no effect 
main.c:971: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:972: warning: passing argument 1 of ‘logwarn’ from incompatible pointer type 
main.c:978: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:984: error: ‘__u32’ undeclared (first use in this function) 
main.c:984: error: expected expression before ‘)’ token 
main.c:984: error: invalid operands to binary * 
main.c:984: error: called object ‘<erroneous-expression>’ is not a function 
main.c:984: error: assignment of read-only location 
main.c:984: error: incompatible types in assignment 
main.c:984: warning: statement with no effect 
main.c:985: error: ‘__u16’ undeclared (first use in this function) 
main.c:985: error: expected expression before ‘)’ token 
main.c:985: error: invalid operands to binary * 
main.c:985: error: called object ‘<erroneous-expression>’ is not a function 
main.c:985: error: assignment of read-only location 
main.c:985: error: incompatible types in assignment 
main.c:985: warning: statement with no effect 
main.c:992: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:993: warning: implicit declaration of function ‘ioctl’ 
main.c:993: warning: implicit declaration of function ‘_IO’ 
main.c:995: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:999: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:1002: warning: passing argument 2 of ‘logsyserror’ from incompatible pointer type 
main.c:1005: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:1013: warning: implicit declaration of function ‘pause’ 
main.c: In function ‘serve_port’: 
main.c:1029: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:1031: error: ‘struct _config’ has no member named ‘realtime’ 
main.c:1041: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:1042: warning: incompatible implicit declaration of built-in function ‘exit’ 
main.c:1047: warning: passing argument 1 of ‘logerr’ from incompatible pointer type 
main.c:1050: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c:1055: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c: In function ‘mexit’: 
main.c:1082: error: ‘struct _config’ has no member named ‘daemon’ 
main.c:1083: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:1085: warning: passing argument 1 of ‘loginfo’ from incompatible pointer type 
main.c:1086: warning: incompatible implicit declaration of built-in function ‘exit’ 
main.c: In function ‘kbdint_handler’: 
main.c:1093: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c: In function ‘setup_kbd_interrupt’: 
main.c:1098: error: storage size of ‘timer_action’ isn’t known 
main.c:1100: error: request for member ‘sa_handler’ in something not a structure or union 
main.c:1100: warning: statement with no effect 
main.c:1101: error: request for member ‘sa_flags’ in something not a structure or union 
main.c:1101: warning: statement with no effect 
main.c:1102: error: request for member ‘sa_mask’ in something not a structure or union 
main.c:1103: error: ‘SIGINT’ undeclared (first use in this function) 
main.c:1098: warning: unused variable ‘timer_action’ 
main.c: In function ‘sigterm_handler’: 
main.c:1107: warning: passing argument 2 of ‘logdebug’ from incompatible pointer type 
main.c: In function ‘setup_daemon_signals’: 
main.c:1112: error: storage size of ‘timer_action’ isn’t known 
main.c:1114: error: request for member ‘sa_handler’ in something not a structure or union 
main.c:1114: warning: statement with no effect 
main.c:1115: error: request for member ‘sa_flags’ in something not a structure or union 
main.c:1115: warning: statement with no effect 
main.c:1116: error: request for member ‘sa_mask’ in something not a structure or union 
main.c:1117: error: ‘SIGTERM’ undeclared (first use in this function) 
main.c:1112: warning: unused variable ‘timer_action’ 
main.c: In function ‘setup_segv’: 
main.c:1124: error: storage size of ‘action’ isn’t known 
main.c:1126: error: request for member ‘sa_handler’ in something not a structure or union 
main.c:1126: warning: statement with no effect 
main.c:1127: error: request for member ‘sa_flags’ in something not a structure or union 
main.c:1127: warning: statement with no effect 
main.c:1128: error: request for member ‘sa_mask’ in something not a structure or union 
main.c:1129: error: ‘SIGSEGV’ undeclared (first use in this function) 
main.c:1124: warning: unused variable ‘action’ 
main.c: In function ‘segv_handler’: 
main.c:1133: error: storage size of ‘action’ isn’t known 
main.c:1136: warning: incompatible implicit declaration of built-in function ‘printf’ 
main.c:1138: error: request for member ‘sa_handler’ in something not a structure or union 
main.c:1138: error: ‘SIG_DFL’ undeclared (first use in this function) 
main.c:1138: warning: statement with no effect 
main.c:1139: error: request for member ‘sa_flags’ in something not a structure or union 
main.c:1139: warning: statement with no effect 
main.c:1140: error: request for member ‘sa_mask’ in something not a structure or union 
main.c:1141: error: ‘SIGSEGV’ undeclared (first use in this function) 
main.c:1133: warning: unused variable ‘action’ 



---

### Post by pandan on 2007-11-21
**[SIZE="3"]I got my PCI Lucent Winmodem to work in Gutsy 7.10![/SIZE]**

**The Community Documentation is the place to start**
There is advice here to run scanmodem.
If it is a Lucent/Agere modem you can find out  where to load the Martian driver from at the bottom of the DialupModemHowto/Lucent page.
< I found that the "ltmodem" installation didn't work under Gutsy so tried Martian>

If you use the Scanmodem tool, it makes a file called AgereDSP.txt
I followed this exactly as root user (you can sudo every command from where it says switch (su) to root if you want) and I can now connect with SUDO WVDIAL.  There is one thing you probably shouldn't do which I've noted below.


In AgereDSP.txt, it tells ubuntu users to download and install "libc6-dev.deb"
Apparently you might be able to install this package from the install CD.
What I did:
Download it from: [http://packages.ubuntu.com](http://packages.ubuntu.com) from the folder "library development"
The website will tell you all it's dependencies (dependent packages). You need to download them too.
('recommends' and 'suggests' packages not necessary)
Do this on another computer that has a internet connection and put all the DEB files on a USB key.

Copy the Deb files to a folder on your ubuntu box.

From the terminal, change directory to that folder and issue the command:
sudo dpkg -i *.deb

Check that the installation has no errors or unresolved dependencies.

Not that libc6-dev.deb is installed properly, we may continue...

Now, you can try install the martian driver according to AgereDSP.txt
Remember: skip the following step in the howto:
>  To automate martian_modem action upon martian_dev loading,
 the following SINGLE line can be added to one of the files /etc/modprobe* 
 or to a new file /etc/modprobe.d/martian 
 install martian_dev  modprobe --ignore-install martian_dev ; /usr/sbin/martian_modem

 However, there is a report that (at least in some Systems), boot up processes
 are slowed. This is associated with bootup testing of potentially needed modules.
 Thus you may choose not to use this automation.
( I found that it stalls my boot and or had toI use a live cd to mount as root and undo the above)
Another way is to load martian_modem with sudo with each session by adding with the session control panel.
It will have to be added to the sudoers list with the NOPASSWD: qualifier. Find out more with "man sudoers"
and edit the file with "sudo visudo"

< this is quite a hassle to do, but hey, you're getting valuable Linux experience in the process! >
< funny thing is, the same modem was heaps easier under 6.06 and 6.10! What happened?!>

Now if you want the **AgereDSP.txt **file I used, here it is.  However, it's better to get the latest scanmodem and use the one it generates.
>  Modems with Lucent/Agere DSP chipsets
 --------------------------------------
A detailed installation report is:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/MarsTest.txt](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/MarsTest.txt) 

 For Lucent/Agere/Xircom modems with DSP (digital signal processing) chipsets Apollo or Mars chip sets, 
LSI Inc. maintainer Soumyendu Sarkar provides occassional updates.
LSI Inc. [http://www.lsi.com/](http://www.lsi.com/), a descendant of Lucent through the former Agere Systems. This code includes a Closed Source component, ltmdmobj.o,  encrypting  copyrighted compression algorithms and other critical Proprietary code.
AMD x86_64  processors are supported, though only in 32 bit mode currently.

The Appolo/Mars support packages have had several variants over the years,
with Linmodems List volunteers contributing to a more friendly package. 
Initially there was only a unitary driver, later split into a ltmodem + ltserial driver pair.
Most recently the ltmdmobj.o has been shifted into a non-driver martian_modem by Alexie Chentsov,
leaving a residual Open Source martian_dev.ko  driver/module.
For Alexie's concept details see: [http://martian.barrelsoutofbond.org](http://martian.barrelsoutofbond.org)
These current packages are available at [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)
This support is robust into the 2.6.20 Linux kernels.

Brad House has reported a problem undering emerging 2.6.22 kernels
which he bypassed by shifting back to the older ltmodem + ltserial format.
See [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02111.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02111.html)

Support packages for 2.6.13  kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

For 2.6.12 and earlier kernels use a package in the folder [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

In addition to general compiling support, there may be needed
additional kernel_header files in /usr/include/  folders.  
For Debian and Ubuntu related Distros these are provided by the package libc6-dev. 
For Ubuntu, search for it at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install after download with:
$ sudo dpkg -i *.deb
For Fedora, the comparable packages (one to all of) have names like:
glibc-headers-2.3.5-10.i386.rpm
glibc-kernheaders-2.4-9.1.94.i386.rpm
glibc-devel-2.3.5-10.i386.rpm
which after download can be installed with:
# rpm -i glibc*.rpm
Do read the  package documentation carefully!!

Here is a detailed instruction set, assuming COMMANDs needing Admin permission are acquired through a preliminary:
$ su root
Ubuntu users would instead initiate such COMMANDs with:
$ sudo COMMAND
=========================================
Get the martian-full-20071011.tar.gz or more recent update from:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

Under Linux:
$ tar zxf  mar*.tar.gz
$ cd  martian-full-20071011

Look around:
$ ls

$ make clean
$ make all
$ su root
# make install

for setup:
# modprobe martain_dev
you can get a report like that below with:
#  dmesg | grep martian
[ 4742.716000] martian loaded - 20071011
[ 4742.716000] "martian_dev": detaching 11c1:445 from serial
[ 4742.732000] "martian_dev": added device 11c1:445 BaseAddress =
0x2040, CommAddres = 0xd4c660ac, irq = 11

The martian_dev provides contact with the hardware.
But most of the COMM smarts are provided by the /usr/sbin/martian_modem. 
Merely test basic sanity with:
# martian_modem --help
# martian_modem --info countries
You can skip these two next time.

You can watch kernel messages with:
#  tail -f /var/log/messages &
The & tells tail to run in the background.
press  RETURN to get the COMMAND prompt back.

Now activate the modem with:
# martian_modem  --country=us
which reports:
 martian: info: Your port is /dev/ttySM0
"martian_dev": serving irqs in module
"martian_dev": martian_modem is attached.
-------
Leave martian_modem running, as it maintains the ports 
and does much of the COMM work!!

Open another Tab/console.  Look at the ports with
$ ls -l /dev/ttySM0 /dev/pts/*
crw--w---- 1 marv tty  136, 0 2007-09-23 22:27 /dev/pts/0
crw--w---- 1 root tty  136, 1 2007-09-23 22:27 /dev/pts/1
crw--w---- 1 marv tty  136, 2 2007-09-23 22:30 /dev/pts/2
lrwxrwxrwx 1 root root     10 2007-09-23 22:27 /dev/ttySM0 -> /dev/pts/1
-------
The ttySM0 is just a convient symbolic link for next steps.
The real and dynamically created /dev/pts/N port,
 that /dev/ttySM0 leads to may have a different N next session.

Next interrogate the modem hardware and start creating a dialout config file:
# wvdialconf  /etc/wvdial.conf
whose report should include:
--------
ttySM0<*1>: ATQ0 V1 E1 -- OK
ttySM0<*1>: ATQ0 V1 E1 Z -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.30
ttySM0<*1>: Speed 4800: AT -- OK
ttySM0<*1>: Speed 9600: AT -- OK
ttySM0<*1>: Speed 19200: AT -- OK
ttySM0<*1>: Speed 38400: AT -- OK
ttySM0<*1>: Speed 57600: AT -- OK
ttySM0<*1>: Speed 115200: AT -- OK
ttySM0<*1>: Speed 230400: AT -- OK
ttySM0<*1>: Speed 460800: AT -- OK
ttySM0<*1>: Max speed is 460800; that should be safe.
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySM0.
--------

If the modem is thus found
# gedit  /etc/wvdial.conf
delete the  ;  and on those lines replace the <xxxx> with your personal info.
add a line:
 Carrier Check  =  no
for a final product like:
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
# without - or spaces:
Phone = 1112223333
# when you need to go through a switchboard with say prefix 9, use a , to pause
# Phone = 9,,1112223333
ISDN = 0
Username = Your_Login_Name
Init1 = ATZ
Password = Your_Password
Modem = /dev/ttySM0
Baud = 460800
#  needed for  /dev/pts/N  ports:
Carrier Check  =  no
# see wvdial info for other options
### End wvdial.conf

Save and  and dialout with:
# wvdial
===========================
This ends the example.

 To automate martian_modem action upon martian_dev loading,
 the following SINGLE line can be added to one of the files /etc/modprobe* 
 or to a new file /etc/modprobe.d/martian 
 install martian_dev  modprobe --ignore-install martian_dev ; /usr/sbin/martian_modem

 However, there is a report that (at least in some Systems), boot up processes
 are slowed. This is associated with bootup testing of potentially needed modules.
 Thus you may choose not to use this automation.

	Support for the former  driver pair, ltmodem + ltserial terminates with 
 2.6.15 kernels. 
	 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
	Call waiting normally specified by, +pcw=1, is not implmented in the Linux drivers.
 	For older ISA card modems, specification of resources through forcing is
 sometimes necessary: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html) 

 The remainder of this section is historical info, awaiting a final edit.
------------------------------------------------------------------------

Support packages for 2.6.n kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/) with folders for
	debian/  containing some installers
	ubuntu/  containing some installers
The ltmodem-8.26b1.tar.gz  and ltmodem-8.31b1.tar.gz are driver compiling resources,
with the 8.31 having support for SMP (symmetric multi processor) motherboards.
These packages are more automated versions of the ltmodem-2.6-alk* packages
The ltmodem-2.6-Nalk.src.rpm packages can be used with rpm using Distros.
	   # rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm  
	   will deposit an installer at:
	        /usr/src/rpm/RPMS//ltmodem-kv_2.6.17-11-386.rpm 	   Check with  
            # ls -l   /usr/src/rpm/RPMS//ltmodem*
	    Then install with:
	    # rpm -i /usr/src/rpm/RPMS//ltmodem-kv_2.6.17-11-386.rpm
	    or similar.

The martian.tar.gz represents a new developmental track, meeting emerging kernel requirements.
See for details:  [http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)
[http://linmodems.technion.ac.il/archive-sixth/msg00142.html](http://linmodems.technion.ac.il/archive-sixth/msg00142.html)
AMD x86_64 competency is provided only bt the martian.

For 2.4.n kernels packages are at [http://ltmodem.heby.de/](http://ltmodem.heby.de/) or [http://phep2.technion.ac.il/linmodems/packages/ltmodem/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/)

 There are some installer packages and also resources for compiling drivers.
 ----------------------
 SuSE/Novell Linux and some other Distros provide compiled drivers +installers.
    Search package lists for ltmodem  
 For other Distros and 2.6.n kernels, see: 

 Packages for compiling drivers are:
 ResourceName                Use for kernel ranges
--------------------------------------------------------------------------------
ltmodem-8.26a.tar.gz         2.4.21 and earlier
ltmodem-8.30a3.tar.gz        2.4.21 and subsequent 2.4.2n kernels
	    which were assembled with a gcc-2.9 comiler
ltmodem-8.31a10.tar.gz     beginning with 2.4.21 and upto about 2.6.8  kernels
martian.tar.gz             2.6.n SMP (symmetic multiprocessor) support not verified.
ltmodem-8.31b1.tar.gz      2.6.n with    SMP support, for some* Systems
ltmodem-8.26b1tar.gz       2.6.n without SMP support
   * While SMP capacity should in principle be without ill effect on single processor systems,
the are some cases of ill effects on single processor systems.

Some additional 2.4.n installers are available from:
[http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some other 2.4.n installers.



---

### Post by renatosilva on 2008-01-07
> **pandan said:**
> [B][SIZE="3"]I found that the "ltmodem" installation didn't work under Gutsy so tried Martian

I use Martian driver. I made a script to automate the whole process. It's just about getting the package, and running the script, then I get a GNOME-PPP shortcut on Desktop and ready to connect with everything installed. It's really nice...

**But I'm curious about ltmodem, Why didn't you get this working with Agere chipset? Everything was fine to me, except when wvdial connected but did not receive DNS servers and related stuff, instead it says the conncetion timed out.**

---

### Post by rolandixor on 2008-04-16
renatosilva-

why don't you post the script if you don't mind.

Secondly.
A general question. why does no one post a deb for this? I don't get!

---

### Post by renatosilva on 2008-04-17
This is the script itself, and attached are all the files required. Read all to understand what you're going to do:)

```

#!/bin/bash

FILE=`readlink -f "$0"`
DIR=`dirname "$FILE"`

source "$DIR/common.sh"

PACKAGE=$1
OPTION=$2

CONFIG_DIR="$DIR/Config"

if [ ! -e "$PACKAGE" ] || [ ! -d "$CONFIG_DIR" ] || [ "$1" == "--help" ]; then
    BASENAME=`basename "$0"`
    echo -e "\n\tRenato's installer for Martian modem driver (v. 2008.1.3)\n"
    echo -e "\tUsage: $BASENAME <driver_source.tar.gz>\n"
    echo -e "\t-y: Assume yes on continue prompts\n"
    echo -e "\tDirectory \"$CONFIG_DIR\" stores additional configs\n"
    exit
fi

LOADER="/etc/rc.local"
MODPROBE="modprobe martian_dev"
DAEMON="martian_modem --daemon"
COMMAND="$MODPROBE && $DAEMON"
EXIT="exit 0"





notify_ln "Compiling and installing Martian driver... " ########################

sudo apt-get install build-essential #linux-headers-`uname -r`
echo
cp "$PACKAGE" "$HOME"
cd "$HOME"
tar -xvzf `basename "$PACKAGE"` 
rm `basename "$PACKAGE"`
cd ./martian
make all
sudo make install
cd "$HOME"
rm -rf "./martian/" # Sudo needed as make creates stuff as root
check_continue $OPTION





notify "Adding driver loading at startup... " ##################################

cd `dirname "$LOADER"`

remove_from_file "$MODPROBE" "$LOADER"
remove_from_file "$DAEMON" "$LOADER"
remove_from_file "$COMMAND" "$LOADER"
remove_from_file "$EXIT" "$LOADER"

sudo_echo_to_file "$COMMAND" "$LOADER"
sudo_echo_to_file "$EXIT" "$LOADER"

say "OK"
show_file "$LOADER"
check_continue $OPTION





notify "Loading driver immediatelly... " #######################################

sudo sh -c "$COMMAND"
say "OK"
check_continue $OPTION





notify_ln "Installing and configuring Gnome PPP... " ###########################

sudo apt-get install gnome-ppp
sudo cp "$CONFIG_DIR/root.wvdial.conf" "/root/.wvdial.conf"
cp "$CONFIG_DIR/gnome-ppp.desktop" "$HOME/Desktop/"



```

---

### Post by rolandixor on 2008-04-17
THANKS!
I'll also see about chmodo+x /bin/laden

wonder if he will let America capture him (as if that will make a difference :-P; the world needs Jesus!)

lol, I digress...
I got it to work (before your script), but the system still whines about not having the modem. I hope this works! :-)

---

### Post by sdowney717 on 2008-04-17
EDIT Add
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=473115](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=473115)

It is a bug, you cant compile martian against this latest kernel for hardy.



actually I cant get it to work for me in Hardy, any ideas??
The script is interesting, but If i run it more than once it will fuss because 
home/scott/martian has been deleted.

```

scott@scott-desktop:~/martian$ make all
make -C kmodule/ modules
make[1]: Entering directory `/home/scott/martian/kmodule'
make -C /lib/modules/2.6.24-16-generic/build M="/home/scott/martian/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/scott/martian/kmodule/martian.o
/home/scott/martian/kmodule/martian.c: In function &#8216;martian_isr&#8217;:
/home/scott/martian/kmodule/martian.c:160: warning: value computed is not used
/home/scott/martian/kmodule/martian.c: In function &#8216;martian_add&#8217;:
/home/scott/martian/kmodule/martian.c:659: error: &#8216;SA_INTERRUPT&#8217; undeclared (first use in this function)
/home/scott/martian/kmodule/martian.c:659: error: (Each undeclared identifier is reported only once
/home/scott/martian/kmodule/martian.c:659: error: for each function it appears in.)
/home/scott/martian/kmodule/martian.c:659: error: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/home/scott/martian/kmodule/martian.c:662: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[3]: *** [/home/scott/martian/kmodule/martian.o] Error 1
make[2]: *** [_module_/home/scott/martian/kmodule] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/scott/martian/kmodule'
make: *** [all] Error 2
scott@scott-desktop:~/martian$ 
```

script error occurs on second run thru, If I manually creat /martian, then no complaints. Of course I still get the error on make

```
scott@scott-desktop:~/lucentmodem$ sudo ./martian.sh martian-full-20071011.tar.gz -y

# Compiling and installing Martian driver... 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

martian-full-20071011/
martian-full-20071011/Makefile
martian-full-20071011/kmodule/
martian-full-20071011/kmodule/Makefile
martian-full-20071011/kmodule/fifo.h
martian-full-20071011/kmodule/kmartian.h
martian-full-20071011/kmodule/marsio.h
martian-full-20071011/kmodule/Module.symvers
martian-full-20071011/kmodule/mfifo.c
martian-full-20071011/kmodule/mfifo.h
martian-full-20071011/kmodule/marsio.c
martian-full-20071011/kmodule/mixspinlock.h
martian-full-20071011/kmodule/martian_ids.c
martian-full-20071011/kmodule/martian.c
martian-full-20071011/ChangeLog
martian-full-20071011/scripts/
martian-full-20071011/scripts/wv.conf
martian-full-20071011/scripts/martian.in
martian-full-20071011/scripts/automate.sh
martian-full-20071011/scripts/remove_outdated.sh
martian-full-20071011/scripts/martian
martian-full-20071011/INSTALL
martian-full-20071011/modem/
martian-full-20071011/modem/common.h
martian-full-20071011/modem/sysdep.c
martian-full-20071011/modem/Makefile
martian-full-20071011/modem/profile.c
martian-full-20071011/modem/watch2.gdb
martian-full-20071011/modem/pty.c
martian-full-20071011/modem/mport.c
martian-full-20071011/modem/link.c
martian-full-20071011/modem/tweakcore.sh
martian-full-20071011/modem/coreadd.c
martian-full-20071011/modem/martian_modem.debug
martian-full-20071011/modem/martian_modem
martian-full-20071011/modem/coresubst.c
martian-full-20071011/modem/main.c
martian-full-20071011/modem/watch.gdb
martian-full-20071011/modem/mport.h
martian-full-20071011/modem/martian_modem.stripped
martian-full-20071011/modem/debug_script.in
martian-full-20071011/modem/log.h
martian-full-20071011/modem/ASWMLICENSE
martian-full-20071011/modem/main.h
martian-full-20071011/modem/isr.c
martian-full-20071011/modem/core_if.c
martian-full-20071011/modem/README
martian-full-20071011/modem/log.c
martian-full-20071011/modem/sysdep.h
martian-full-20071011/modem/watch4.gdb
martian-full-20071011/modem/watch3.gdb
martian-full-20071011/modem/tweakrelocsdynamic.c
martian-full-20071011/modem/smp.c
martian-full-20071011/modem/ltmdmobj.o
martian-full-20071011/modem/mixspinlock.h
martian-full-20071011/modem/session.c
martian-full-20071011/modem/watch.h
martian-full-20071011/modem/elf386tweakrelocs.c
martian-full-20071011/modem/dumpers.c
martian-full-20071011/README
martian-full-20071011/Concept
martian-full-20071011/martian.h
./martian.sh: line 40: cd: ./martian: No such file or directory
make: *** No rule to make target `all'.  Stop.
make: *** No rule to make target `install'.  Stop.


```

---

### Post by renatosilva on 2008-04-17
> **sdowney717 said:**
> ...

That's weird, if you run the script again, it should extract the .tar.gz to the same ./martian directory, but it seems in your example it was extracted to martian-full-20071011 instead, don't know why.

About make error, try installing this package: linux-headers-`uname -r` (uncomment it from the script)

---

### Post by sdowney717 on 2008-04-18
tried that. Did not make any difference. 
I am running hardy latest beta.

This used to work but I quess not for this kernel in Hardy.
Maybe it will get fixed someday with a new version of martian.

---

