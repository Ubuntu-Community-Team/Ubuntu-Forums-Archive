---
title: "Atheros not being picked up and madwifi not installing correctly"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Sanelora on 2008-09-19
Hey guys, sorry about the non-descriptive title. I honestly don't know what else to say!

First of all, I would like to let you know that the PC that has Ubuntu on it **does not** have access to the internet until the WiFi is back up and running. It will not have access to a wired connection at all :(. I have a laptop running windows vista on the wifi Network sitting next to my PC to help with the setup.

I have been reading about installing the Madwifi drivers and such to solve this problem so I downloaded the actual program and tried to install it.

During the "make" step of the installation I got the following error (I am exceptionally new to, Ubuntu, Linux or indeed any Unix system so please point out if I have made any stupid steps.):

```
james@james-desktop:~/madwifi-0.9.4$ sudo make

Checking requirements... ok.

Checking kernel configuration... ok.

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/james/madwifi-0.9.4 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  HOSTCC  /home/james/madwifi-0.9.4/ath_hal/uudecode

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/james/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'

make[3]: *** [/home/james/madwifi-0.9.4/ath_hal/uudecode] Error 1

make[2]: *** [/home/james/madwifi-0.9.4/ath_hal] Error 2

make[1]: *** [_module_/home/james/madwifi-0.9.4] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

make: *** [modules] Error 2

```

this has had me pulling out my hair for about 3 days.

After this has been resolved, would it be possible to have someone give me a step by step walkthrough of finishing the installation and setup of my wireless card?

Much appreciated in advance guys :)

Cheers,
Sane

---

### Post by sggarps on 2008-09-21
I have exactly the same problem, along with the lack of internet. Seems like catch 22.

---

### Post by thomas228 on 2008-09-25
> **Sanelora said:**
> Hey guys, sorry about the non-descriptive title. I honestly don't know what else to say!

First of all, I would like to let you know that the PC that has Ubuntu on it **does not** have access to the internet until the WiFi is back up and running. It will not have access to a wired connection at all :(. I have a laptop running windows vista on the wifi Network sitting next to my PC to help with the setup.

I have been reading about installing the Madwifi drivers and such to solve this problem so I downloaded the actual program and tried to install it.

During the "make" step of the installation I got the following error (I am exceptionally new to, Ubuntu, Linux or indeed any Unix system so please point out if I have made any stupid steps.):

```
james@james-desktop:~/madwifi-0.9.4$ sudo make

Checking requirements... ok.

Checking kernel configuration... ok.

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/james/madwifi-0.9.4 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'

  HOSTCC  /home/james/madwifi-0.9.4/ath_hal/uudecode

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory

/home/james/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/james/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'

/home/james/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'

make[3]: *** [/home/james/madwifi-0.9.4/ath_hal/uudecode] Error 1

make[2]: *** [/home/james/madwifi-0.9.4/ath_hal] Error 2

make[1]: *** [_module_/home/james/madwifi-0.9.4] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

make: *** [modules] Error 2

```

this has had me pulling out my hair for about 3 days.

After this has been resolved, would it be possible to have someone give me a step by step walkthrough of finishing the installation and setup of my wireless card?

Much appreciated in advance guys :)

Cheers,
Sane

> **sggarps said:**
> I have exactly the same problem, along with the lack of internet. Seems like catch 22.

This my second try at a reply - lost an hour:(

The following is quoted from Nicedude's Post #1 
AR5007 Atheros Madwifi Hardy 8.04 32BIT I386 INSTALL INSTRUCTIONS STEP BY STEP 

"""""""
-= STEP 2 =- Get Needed Packages For Building Stuff
Get 2 packages you will need to build drivers for your system by searching by name for the following two softwares in the synaptic package manager ( System > Administration > Synaptic package manager )

make
build-essential

click both of those for install and apply to install them. You will need these in a second so your system can build new drivers from the madwifi source you will be downloading you will also need these in the future to build any other drivers or programs from source.
""""""""""
Assuming you installed Ubuntu with a CDrom you can use it as a source by System > Administration > Synaptic package manager -> Settings -> Repositories -> Ubunta Software tab and check off **Installable from CD-ROM/DVD** box. Close and your cdrom becomes a source.
"""""""
Once in the synaptic package manager you can use the big button that says search and make sure to search by name and description 
""""""""
Search for build-essential and make
Mark them for installation with all their dependecies and apply

Open a terminal, cd to your Madwifi directory, and run "sudo make clean" to clean out the the last "sudo make" leftovers.
"""""""""
now run 
"sudo make" 
wait for it to complete and if it does so without errors  

next copy and run 
"sudo make install"
 
:confused:If you still get errors you'll probably have to install

libc6-dev_2.7-10ubuntu3_i386.deb from http://packages.ubuntu.com/hardy/i386/libc6-dev/download :guitar:

after that completes copy and run 
"sudo modprobe ath_pci" 

which will load the driver you just made from the patched source ( You now have become your own restricted driver manager ).


-= STEP 6 =- Set Driver Modules To Load At Bootup
I also had to edit the following file /etc/modules, use this command to edit the file

"sudo gedit /etc/modules"

and add the following 2 lines to the end of the ones already there, and then save the file and exit Gedit.

ath_hal
ath_pci 

this will load your cards modules on system startup
"""""""
Hope this makes sense to you as it worked for my Toshiba Satellite A205 A55 laptops.
I'm just a newbie on Ubunta but I need to get away from windows so I'm trying hard.

I did have to download "wicd_1.5.2_all.deb", uninstall "network-manager" using Synaptic package manager and using File Browser activate Package Installer by double clicking on "wicd_1.5.2_all.deb" and apply.
Good luck

---

