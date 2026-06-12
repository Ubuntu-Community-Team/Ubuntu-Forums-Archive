---
title: "[SOLVED] ndiswrapper won't install (errors shown)"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by dougtron on 2007-10-07
Hello, I'm trying to install ndiswrapper but I keep getting the following errors. (I get errors when I do 'make' by its self, but these are the errors from 'make install')

```
doug@doug-laptop:~$ su -
Password: 
root@doug-laptop:~# cd /home/doug/ndiswrapper-1.48
root@doug-laptop:/home/doug/ndiswrapper-1.48# make install
make -C driver install
make[1]: Entering directory `/home/doug/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/doug/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
make[1]: Leaving directory `/home/doug/ndiswrapper-1.48/driver'
make -C utils install
make[1]: Entering directory `/home/doug/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â€˜size_tâ€™
loadndisdriver.c: In function â€˜load_fileâ€™:
loadndisdriver.c:67: error: â€˜size_tâ€™ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â€˜;â€™ before â€˜sizeâ€™
loadndisdriver.c:68: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:71: warning: implicit declaration of function â€˜basenameâ€™
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â€˜openâ€™
loadndisdriver.c:73: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜syslogâ€™
loadndisdriver.c:75: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:75: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜strerrorâ€™
loadndisdriver.c:75: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:76: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â€˜fstatâ€™
loadndisdriver.c:81: warning: implicit declaration of function â€˜closeâ€™
loadndisdriver.c:84: error: â€˜sizeâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â€˜mmapâ€™
loadndisdriver.c:86: error: â€˜PROT_READâ€™ undeclared (first use in this function)
loadndisdriver.c:86: error: â€˜MAP_PRIVATEâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â€˜MAP_FAILEDâ€™ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â€˜strncpyâ€™
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:95: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:96: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:69: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜parse_setting_lineâ€™:
loadndisdriver.c:109: warning: implicit declaration of function â€˜isspaceâ€™
loadndisdriver.c:115: warning: implicit declaration of function â€˜strchrâ€™
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â€˜strchrâ€™
loadndisdriver.c:115: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:118: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â€˜strlenâ€™
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c: In function â€˜read_conf_fileâ€™:
loadndisdriver.c:150: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:151: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:151: error: â€˜configâ€™ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â€˜lstatâ€™
loadndisdriver.c:158: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:160: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â€˜sscanfâ€™
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:178: warning: implicit declaration of function â€˜fopenâ€™
loadndisdriver.c:178: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function â€˜fgetsâ€™
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:205: warning: implicit declaration of function â€˜fcloseâ€™
loadndisdriver.c:150: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_bin_fileâ€™:
loadndisdriver.c:217: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:217: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function â€˜tolowerâ€™
loadndisdriver.c:221: warning: implicit declaration of function â€˜chdirâ€™
loadndisdriver.c:222: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:224: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:232: warning: implicit declaration of function â€˜ioctlâ€™
loadndisdriver.c:232: warning: implicit declaration of function â€˜_IOWâ€™
loadndisdriver.c:232: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜load_driverâ€™:
loadndisdriver.c:249: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:249: error: â€˜driver_dirâ€™ undeclared (first use in this function)
loadndisdriver.c:251: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:255: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:255: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:257: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:259: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function â€˜opendirâ€™
loadndisdriver.c:267: warning: implicit declaration of function â€˜mallocâ€™
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function â€˜mallocâ€™
loadndisdriver.c:271: warning: implicit declaration of function â€˜memsetâ€™
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:280: warning: implicit declaration of function â€˜readdirâ€™
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function â€˜statâ€™
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â€˜S_ISREGâ€™
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function â€˜strcasecmpâ€™
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function â€˜strcpyâ€™
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function â€˜strcpyâ€™
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:318: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable â€˜statbufâ€™
loadndisdriver.c:344: error: expected expression before â€˜structâ€™
loadndisdriver.c:346: warning: implicit declaration of function â€˜closedirâ€™
loadndisdriver.c:348: warning: implicit declaration of function â€˜freeâ€™
loadndisdriver.c:355: warning: implicit declaration of function â€˜munmapâ€™
loadndisdriver.c:355: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:355: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:357: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:357: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c: In function â€˜get_deviceâ€™:
loadndisdriver.c:367: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:370: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:370: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:373: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:374: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function â€˜snprintfâ€™
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:367: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_deviceâ€™:
loadndisdriver.c:419: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:419: error: â€˜dirâ€™ undeclared (first use in this function)
loadndisdriver.c:423: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:423: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:426: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:427: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:429: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜get_ioctl_deviceâ€™:
loadndisdriver.c:464: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:464: error: â€˜proc_miscâ€™ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function â€˜strstrâ€™
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function â€˜strstrâ€™
loadndisdriver.c:473: warning: implicit declaration of function â€˜strtolâ€™
loadndisdriver.c:473: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:483: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:483: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function â€˜unlinkâ€™
loadndisdriver.c:489: warning: implicit declaration of function â€˜mknodâ€™
loadndisdriver.c:489: error: â€˜S_IFCHRâ€™ undeclared (first use in this function)
loadndisdriver.c:489: error: â€˜MISC_MAJORâ€™ undeclared (first use in this function)
loadndisdriver.c:490: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:495: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c: In function â€˜mainâ€™:
loadndisdriver.c:511: warning: implicit declaration of function â€˜openlogâ€™
loadndisdriver.c:511: error: â€˜LOG_PERRORâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_CONSâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_DEBUGâ€™ undeclared (first use in this function)
loadndisdriver.c:513: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function â€˜strncmpâ€™
loadndisdriver.c:517: warning: implicit declaration of function â€˜printfâ€™
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
loadndisdriver.c:527: warning: implicit declaration of function â€˜atoiâ€™
loadndisdriver.c:542: warning: implicit declaration of function â€˜atofâ€™
loadndisdriver.c:549: warning: implicit declaration of function â€˜strcmpâ€™
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:590: warning: implicit declaration of function â€˜closelogâ€™
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/doug/ndiswrapper-1.48/utils'
make: *** [install] Error 2
root@doug-laptop:/home/doug/ndiswrapper-1.48# 


```

also sorry i think some of the text looks weird because im opening it with windows. any advice on what's going wrong?

thanks, doug.

---

### Post by lebishop on 2007-10-07
I'm not certain what is actually going on, but the has got some strange characters. Weird?

---

### Post by dougtron on 2007-10-07
Yeah sorry, I opened the linux text file in windows...so there was probably some things that didn't transfer over correctly...but I figured you could get the jist of it. Maybe. I'm confused. I also just realized I have a AMD64 cpu and didn't download that version of Ubuntu....I'm wondering if that is the cause of some of my problems. (New laptop, dual booting Vista + Ubuntu)

---

### Post by lionround on 2007-10-07
You need to go to Synaptic Package Manager and install build-essential.

After that you can rerun ALL of the install instructions for the ndiswrapper.  

That worked for me.  Hope it works for you too.

---

### Post by kevdog on 2007-10-07
sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by dougtron on 2007-10-08
Hey guys sorry to be a pain.... I tried to go into the Synaptic Package Manager but it wasn't listed there,

so then I tried kevdog's terminal installing commands.... but it "couldn't find any package whose name or description matched "build-essential"...."

can I download the build-essentials somewhere and install them that way? Also I'm running 7.04 Fiesty Fawn if you were wondering.

Thanks a lot, Doug.

---

### Post by kevdog on 2007-10-08
What shows up when you do 

sudo apt-cache search build-essential
sudo apt-cache search essential

Weird.

[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)

---

### Post by dougtron on 2007-10-08
```
doug@doug-laptop:~$ sudo apt-cache search build-essential
doug@doug-laptop:~$ sudo apt-cache search essential
coreutils - The GNU core utilities
gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" set
python-minimal - A minimal subset of the Python language (default version)
python2.5-minimal - A minimal subset of the Python language (version 2.5)
perl-base - The Pathologically Eclectic Rubbish Lister
libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set
system-services - definitions of essential system services
startup-tasks - definitions of essential tasks to run on startup
groff-base - GNU troff text-formatting system (base system components)
gstreamer0.10-plugins-base - GStreamer plugins from the "base" set


```

as you can see, searching build essential didn't give me any response whatsoever.

---

### Post by dougtron on 2007-10-08
Also, I just tried to install build-essentials via the link you sent me, when opening the installer it said "Error: Dependency is not satisfiable: libc6-dev|libc-dev" and won't let me click the Install Package button.

---

### Post by kevdog on 2007-10-08
For pete's sake

Ok try this -- do you have the installation CD handy.  Hopefully you do 
Stick it in the driver and do the following:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

---

### Post by dougtron on 2007-10-08
Haha I do indeed have the cd handy, I'll try that quick. Thanks for helping me out with all of this, I'll let you know how it goes.

---

### Post by dougtron on 2007-10-08
Wooo...it liked something about that. Got ndiswrapper to install! Next step is all the drama with drivers but I think I can figure that out ;) haha. Thanks again!

---

### Post by kvonb on 2007-10-08
Don't bother with the 64bit version of Ubuntu, it can cause a lot of problems, especially for the inexperienced!

Why not simply install the official ndiswrapper package, rather than compiling a new version?

What version of Ubuntu are you running?

Maybe you need to enable all the repos, on your main menu goto System -> Administration -> Software Sources, and make sure all the boxes are ticked, then run an update.

Hmm, just a thought, but I'm *assuming* that you can actually download stuff from the Internet, but seeing as you are trying to get ndiswrapper working it might be safer to assume that you cannot actually connect yet!!!

It can be done though, get someone to email you a copy of ndiswrapper-common and ndiswrapper-utils-1.9, you can then simply open them from your desktop and install them, but install -common first.

I've attached the necessary files to this message, download them and copy them to your Ubuntu desktop.  The ones I attached will work in both Feisty and Gutsy (I tried it myself).

Let me know if you need more instructions.

Regards, KEv :)

---

### Post by kvonb on 2007-10-08
oops, bit slow there :(

---

### Post by kevdog on 2007-10-08
After the process is done, just be sure to edit your /etc/apt/sources and remove the line that has the cd-rom statement.  You dont need it anymore.

---

