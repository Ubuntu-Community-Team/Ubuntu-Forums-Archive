---
title: "Madwifi on Hardy Heron"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by hotel86 on 2008-08-16
Having trouble getting Madwifi driver to install on Ubuntu 8.10 Hardy Heron can someone please give me a step by step...
Toshiba Sattelite AMD Turion 64 X2 TL-64 vista dual boot with Atheros wireless adapter...
any and all help would be greatly appreciated, thanks

  -hotel86

---

### Post by hotel86 on 2008-09-04
here is some more information on what I keep getting as returns when I attempt to install.  I have used several different install commands that I have found in a couple books I have and that I found online...

--hotel

hotel@hotel-laptop:~$ cd /home/hotel/madwifi-0.9.4

hotel@hotel-laptop:~/madwifi-0.9.4$ make

Checking requirements... ok.

Checking kernel configuration... ok.

make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/hotel/madwifi-0.9.4 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'

  CC [M]  /home/hotel/madwifi-0.9.4/ath/if_ath.o

  CC [M]  /home/hotel/madwifi-0.9.4/ath/if_ath_pci.o

  LD [M]  /home/hotel/madwifi-0.9.4/ath/ath_pci.o

  CC [M]  /home/hotel/madwifi-0.9.4/ath_hal/ah_os.o

  HOSTCC  /home/hotel/madwifi-0.9.4/ath_hal/uudecode

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c: At top level:

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'

/home/hotel/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'

make[3]: *** [/home/hotel/madwifi-0.9.4/ath_hal/uudecode] Error 1

make[2]: *** [/home/hotel/madwifi-0.9.4/ath_hal] Error 2

make[1]: *** [_module_/home/hotel/madwifi-0.9.4] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'

make: *** [modules] Error 2

hotel@hotel-laptop:~/madwifi-0.9.4$ 

at this point I ran the command “make clean”




hotel@hotel-laptop:~/madwifi-0.9.4$ make clean

for i in ath/ ath_hal/ ath_rate/ net80211/; do \

		make -C $i clean; \

	done

make[1]: Entering directory `/home/hotel/madwifi-0.9.4/ath'

rm -f *~ *.o *.ko *.mod.c .*.cmd

rm -f .depend .version .*.o.flags .*.o.d

rm -rf .tmp_versions

make[1]: Leaving directory `/home/hotel/madwifi-0.9.4/ath'

make[1]: Entering directory `/home/hotel/madwifi-0.9.4/ath_hal'

rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd

rm -f .depend .version .*.o.flags .*.o.d

rm -rf .tmp_versions

make[1]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_hal'

make[1]: Entering directory `/home/hotel/madwifi-0.9.4/ath_rate'

for i in amrr/ onoe/ sample/ minstrel/; do \

		make -C $i clean; \

	done

make[2]: Entering directory `/home/hotel/madwifi-0.9.4/ath_rate/amrr'

rm -f *~ *.o *.ko *.mod.c

rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd

rm -rf .tmp_versions

make[2]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_rate/amrr'

make[2]: Entering directory `/home/hotel/madwifi-0.9.4/ath_rate/onoe'

rm -f *~ *.o *.ko *.mod.c

rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd

rm -rf .tmp_versions

make[2]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_rate/onoe'

make[2]: Entering directory `/home/hotel/madwifi-0.9.4/ath_rate/sample'

rm -f *~ *.o *.ko *.mod.c

rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd

rm -rf .tmp_versions

make[2]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_rate/sample'

make[2]: Entering directory `/home/hotel/madwifi-0.9.4/ath_rate/minstrel'

rm -f *~ *.o *.ko *.mod.c

rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd

rm -rf .tmp_versions

make[2]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_rate/minstrel'

make[1]: Leaving directory `/home/hotel/madwifi-0.9.4/ath_rate'

make[1]: Entering directory `/home/hotel/madwifi-0.9.4/net80211'

rm -f *~ *.o *.ko *.mod.c

rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd

rm -rf .tmp_versions

make[1]: Leaving directory `/home/hotel/madwifi-0.9.4/net80211'

make -C ./tools  clean

make[1]: Entering directory `/home/hotel/madwifi-0.9.4/tools'

rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info core a.out

make[1]: Leaving directory `/home/hotel/madwifi-0.9.4/tools'

rm -rf .tmp_versions

rm -f *.symvers svnversion.h


And I also got the following returns as I ran the commands sudo apt-get install...
and the sudo aptitude install...
and sudo aptitude install... “”

hotel@hotel-laptop:~/madwifi-0.9.4$ sudo apt-get install madwifi

[sudo] password for hotel: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package madwifi

hotel@hotel-laptop:~/madwifi-0.9.4$ cd /home/hotel

hotel@hotel-laptop:~$ sudo apt-get install madwifi-0.9.4

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package madwifi-0.9.4

hotel@hotel-laptop:~$ sudo aptitude install madwifi-0.9.4

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Initializing package states... Done

Writing extended state information... Done

Building tag database... Done             

Couldn't find any package whose name or description matched "madwifi-0.9.4"

Couldn't find any package whose name or description matched "madwifi-0.9.4"

No packages will be installed, upgraded, or removed.

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Writing extended state information... Done

Reading package lists... Done             

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done      

hotel@hotel-laptop:~$ cd /home/hotel

hotel@hotel-laptop:~$ sudo aptitude install madwifi-0.9.4

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done      

Couldn't find any package whose name or description matched "madwifi-0.9.4"

Couldn't find any package whose name or description matched "madwifi-0.9.4"

No packages will be installed, upgraded, or removed.

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done      

hotel@hotel-laptop:~$ cd~

bash: cd~: command not found

hotel@hotel-laptop:~$ cd

hotel@hotel-laptop:~$ sudo aptitude install "madwifi"

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done      

Couldn't find any package matching "madwifi".  However, the following

packages contain "madwifi" in their description:

  linux-restricted-modules-2.6.24-16-generic 

Couldn't find any package matching "madwifi".  However, the following

packages contain "madwifi" in their description:

  linux-restricted-modules-2.6.24-16-generic 

No packages will be installed, upgraded, or removed.

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initializing package states... Done

Building tag database... Done

---

### Post by sinclair86 on 2008-09-28
We'll take this a step at a time. First thing that needs to be done is you need build essentials

```
sudo apt-get install build-essential
```

that should take care of your missing header files and such. Then try to recompile and post what you got.

On a side note:

sudo apt-get install is for installing packages from the repository not compiling source. That why you got "E: Couldn't find package madwifi-0.9.4"

---

### Post by hotel86 on 2008-09-28
> **sinclair86 said:**
> We'll take this a step at a time. First thing that needs to be done is you need build essentials

```
sudo apt-get install build-essential
```

that should take care of your missing header files and such. Then try to recompile and post what you got.

On a side note:

sudo apt-get install is for installing packages from the repository not compiling source. That why you got "E: Couldn't find package madwifi-0.9.4"
  I have experience in programming but this is all new to me...I am a very new user to Ubuntu and linux in general so please excuse my question of how I know that its in a repository or a compiling source?

---

### Post by hotel86 on 2008-09-28
ok so i just ran that command and it said that it couldn't find package build essential...

---

### Post by sinclair86 on 2008-09-28
let me just get this out of the way. is this a laptop or desktop? whichever it is is it connected to the internet right now not using the wireless card? if so try


try 
```
sudo apt-get update
``` 
then
```
sudo apt-get install build-essential
``` [no spaces its build-essential]


if there is a make file or you have to run make install you are compiling from the source. The repository are packages that ubuntu maintains. when you download them(apt-get install ...) they automatically build and install.

---

### Post by hotel86 on 2008-09-28
That computer is a laptop and it does not have a network connection at all other than in windows im on a different computer right now on vista

---

### Post by hotel86 on 2008-09-28
I forgot to say that when ever i try to run the commands in the make file i get the returns that I posted above from before

---

### Post by sinclair86 on 2008-09-28
Ok. Any possibility that you can connected your laptop to your router with an ethernet cord and boot into ubuntu?

---

### Post by hotel86 on 2008-09-28
no because my internet connection is on someone elses router that I don't have direct physical access to...

---

### Post by sinclair86 on 2008-09-28
LOL! I like that. K well we are going to this the semi difficult way. Do you have a usb stick where you can download files from the computer you are on now and transfer them to the ubuntu computer? also paste the output of 

```
uname -a
``` (need to know the architecture/headers)

---

### Post by hotel86 on 2008-09-28
yeah I can definatly do that although this machine is not in the greatest condition and has not very much ram so it will probably take a while

---

### Post by sinclair86 on 2008-09-28
eek. Dont know if I confused you or not. I meant the files you are going to need for this to work you are going to have to download from the web on the computer you are on now and then to the usb stick then to the ubuntu computer. 

in ur ubuntu computer type```
uname -a
``` and post the out put

---

### Post by hotel86 on 2008-09-28
ok so i just ran that command and got just this single line returned:  
2.6.24-16 generic #1 smp Thur Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by hotel86 on 2008-09-28
ya my network connected computer is a 4 year old gateway m275 tablet pc with 512 gb ram and very little hdd space left (out of 20 gb) and its already slow so a file that is of substantial size will take a while even if only to a usb... its still slow thats why i never use this machine...

---

### Post by sinclair86 on 2008-09-28
ok cool. dont worry about the space the file sizes are small and you can save them right to the usb. 

go here ```
http://packages.ubuntu.com/hardy/i386/build-essential/download
``` and click on of the download links. stick it on ur ubuntu computer and double click on it and it should self install

then try [while you are in the madwifi folder]
```
make
```

---

### Post by hotel86 on 2008-09-28
ya i have an amd turion 64 x2 not an intel so shouldnt that be a link for the i686 package rather than the i386...

---

### Post by sinclair86 on 2008-09-28
oops sorry lol i even saw that in the output lolol

```
http://packages.ubuntu.com/hardy/amd64/build-essential/download
```

i know thats not going to solve it all ((ur going to need libdev etc) thats why I like apt-get it gets the dependencies as well) just post the output of make

---

### Post by hotel86 on 2008-09-28
ok so I tried the amd one and it returned an error that said that i  have the wrong architecture 'amd64'

Then I used the i386 version and that returned an even longer error message...

---

### Post by sinclair86 on 2008-09-28
hrmph what was the error message? do you have aol instant messenger? might be easier to talk that way then having keep check the boards

---

### Post by hotel86 on 2008-09-28
no sorry i only have msn and yahoo

---

### Post by sinclair86 on 2008-09-28
bah... anyways what was the error message from build-install? did you install the 64 bit distro?

---

