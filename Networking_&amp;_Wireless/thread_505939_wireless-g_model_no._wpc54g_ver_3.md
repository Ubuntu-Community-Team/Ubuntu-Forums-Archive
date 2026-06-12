---
title: "wireless-g model no. wpc54g ver 3"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by 01queen on 2007-07-20
hey. so i got a linksys wireless-g notbook adapter model number WPC54G
right now I just kindof plugged it in..and went into networking and i saw it said wireless connection, so i enabled it and all that jazz. well I see "new-host" on my router(WINDOWS COMP) and i did ifconfig and it gives me 127.0.0.1 (what i learned in linux..that's your comp. local address. haha) so, i restarted, and still no luck.  the power light is on(but no link light), and up in the top at the 2 little comptuers, i hover over it it says "network conection:lo" not sure what that is..also when I click on it the connection properties come up w/ the status of idle but it says 2 packets sent & received...
 
but yea. any advice?  Thanks:)

---

### Post by kevdog on 2007-07-21
I have same card.  Originally had it working with bcm43xx and fwcutter drivers, now have installed ndiswrapper with linksys driver.  I have a feeling your going to have to try either solution.

---

### Post by 01queen on 2007-07-21
and can you give me directions? lol. I took a intro linux class, but I didnt really like it, so I kindof just did enough to get me by, now I'm having to take an indept linux class, and actually learn the stuff, and putting it on the laptop I was thinking what the heck...trial & error..

how do you install it. step by step?  =) thanks again!

---

### Post by 01queen on 2007-07-22
this is what i get in the termial window

queen@Queen:~$ lspci -nn


00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:02.0 0607: 104c:ac1b (rev 03)
00:02.1 0607: 104c:ac1b (rev 03)
00:03.0 0780: 11c1:0449 (rev 01)
00:06.0 0401: 1013:6003 (rev 01)
00:07.0 0680: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 03)
01:00.0 0300: 10c8:0006
02:00.0 0200: 1113:1216 (rev 11)


queen@Queen:~$ lshw -C network


WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: EN-1216 Ethernet Adapter
       vendor: Accton Technology Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 11
       serial: 00:04:e2:7a:f5:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip ip=192.168.2.2 multicast=yes
       resources: ioport:1000-10ff iomemory:12000000-120003ff irq:11


but at the time my wireless card is not in, only my wired card is in. i ahve 2 and they don't both fit in at the same time.

---

### Post by kevdog on 2007-07-22
Can you stick your wireless card in and repeat the process -- it would really help me.  Thanks.

---

### Post by 01queen on 2007-07-22
queen@Queen:~$ lspci -nn
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:02.0 0607: 104c:ac1b (rev 03)
00:02.1 0607: 104c:ac1b (rev 03)
00:03.0 0780: 11c1:0449 (rev 01)
00:06.0 0401: 1013:6003 (rev 01)
00:07.0 0680: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 03)
01:00.0 0300: 10c8:0006
02:00.0 0280: 14e4:4318 (rev 02)


queen@Queen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:70:4a:80:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:12000000-12001fff irq:11



do i need to enable it and then do it again?

---

### Post by kevdog on 2007-07-22
Before we get going, do you have any Windows XP drivers for the card?? And do you have access to a computer -- either this one or another one -- with internet access.  We are going to have to download some files from the internet, and transfer to Ubuntu via a USB stick

---

### Post by 01queen on 2007-07-22
yes. i have the cd that came w/ the linksys and I have my desktop pc which has xp on it.  
what i find interesting, is that I can see "new host" on my router interface I use on my windows xp computer.


i put the cd in my win xp computer and it will not go where i can see the files on it.  not sure why?:(

never mind it's just really slow

---

### Post by 01queen on 2007-07-22
so....any ideas?

---

### Post by kevdog on 2007-07-22
Ok, these directions are very involved.  Dont get overwhelmed by looking at them at first.  You are going to learn a lot about Ubuntu/Linux in general by doing the steps.  They are very reproducible so just take it a step at a time.  All commands are typed at the command line.

Lets first blacklist the bcm43xx module currently associated with your card:
```
gksu gedit /etc/modprobe.d/blacklist
```

At bottom of file add the following:
```
blacklist bcm43xx
```

Save the file and exit.

We are going to try to enable your wireless card to work via the use of ndiswrapper.  Despite what you have read about ndiswrapper, it works very well, although its a pain to set up.  We are going to compile the ndiswrapper package from source -- you may have never done this before, but it is straightforward.

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside the ~/ndiswrapper directory (Can you nautilis to do this)

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```
I cant remember the exact output but make sure you dont get any errors.

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by 01queen on 2007-07-22
I get errors:(

when I get to 

tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
-->sudo make install


and when I do ndiswrapper -v it says command not found.

---

### Post by 01queen on 2007-07-22
when i get to the sudo make install. this is what i get.

queen@Queen:~/ndiswrapper/ndiswrapper-1.47$ sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/queen/ndiswrapper/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/queen/ndiswrapper/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/queen/ndiswrapper/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/queen/ndiswrapper/ndiswrapper-1.47/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/queen/ndiswrapper/ndiswrapper-1.47/utils'
make: *** [install] Error 2
queen@Queen:~/ndiswrapper/ndiswrapper-1.47$

---

### Post by kevdog on 2007-07-22
Hmm  seems like your are missing some linux header files -- Im guessing.

Put the CD back into the drive and type the following:
> 
sudo aptitude install linux-headers-`uname -r`

Then 
> cd ~/ndiswrapper/ndiswrapper-1.47
make distclean
make
sudo make install

Hopefully that will work!!

---

### Post by 01queen on 2007-07-23
I think I am getting it. no errors so far. i started over doing it with internet connection w/o the wirless card in. will keep you updated:)

---

### Post by 01queen on 2007-07-23
okay so I finally got everything done without any errors. yay! I tried to type the last command(to restart) and it wouldnt recognize the shutdown -r row command, so I restarted it manually.  

well when I get it up..the wirelss connection is not configured, so I click enable this connection and leave the ESSID name blank and doing automatic configuration of DHCP. and it still does not configure it or connect to the internet.


also on my cd, there are only a folder called 9x and NT folders under Drivers, so I used the 9x, is that correct or okay? I did not see a XP folder even tho the package says it's windows 98s, ME, NT & XP compatiable

---

### Post by 01queen on 2007-07-23
never mind. I clicked on the little computers at the top and I saw wlan0 and clicked it and it's wireless yay!

so what do I do whenever I go somewhere like my sister's apartment & she has password protections..how can I use hers?

also do I need to name the ESSID the actual name of the SSID like for windows

My network at home is "Wireless"

well does the ESSID have to be wireless in order to connect to it?

also. why do I have to activate my wireless connection*through system>>admin>>networking*

Thanks again for all your help!!!! I hope I contiune to learn linux & love it:)

---

### Post by kevdog on 2007-07-23
I think I understand the problem -- I think it is still with the header files.

The correct syntax is `uname -r` and not 'uname -r'

See the difference??  Its not single quotes, its an accent.

---

### Post by 01queen on 2007-07-23
that matters even tho it works? or does that make it not have to know the ESSID name?


can I fix that without having to re-do the whole stuff...

if so..how?

---

### Post by kevdog on 2007-07-23
Please post your /etc/network/interfaces and /etc/iftab files.  The ESSID does not need to be broadcast in order for you to connect to it. To see the networks in your area you can do:
iwlist scan

It should show you your network, and possibly others!

---

### Post by 01queen on 2007-07-23
i will post the /etc/network/interfaces and /etc/iftab files in the morning. one quick question.

do the iwlist scan at the interface or how do you do that? and connect to them, if they are password protected?  

thanks again for all your help, you do't know how much it means to me

---

### Post by kevdog on 2007-07-23
I really dont understand your question.

iwlist scan -- This command scans for wireless networks using your wireless network interface (ie wlan0).  It will show available wireless networks in the area.

As far as connecting to encrypted networks, I believe you are using network manager (GUI icon in system tray), to currently connect to your network???  Network manager by default has WEP capabilities built-in.  With a few modifications and by installation of the wpasupplicant package, WPA networks can also be used.

If your not using network manager, there are other GUI interfaces available (wicd, wifi-radar), or there is the old tried and true manual method (modifications of the /etc/network/interfaces file), that will also allow you to connect to both encrypted and unencrypted network.

---

### Post by 01queen on 2007-07-24
okay my question is...the ESSID name under Networking..does that have to be filled in to connect??

iwlist scan is typed in the command window?  The way I connected was the little computers at the top and I clicked on it, and changed it to wlan0

does that make sense?

---

### Post by kevdog on 2007-07-24
If the ESSID is broadcast, your computer should just find the network, or list the network without you having to type it!

---

### Post by 01queen on 2007-07-24
it will not connect inless I have the correct ESSID name in the networking if I go to Systems>>Admin>>Networking....Am I  doing it wrong?? 

I did a scan threw the terminal window, but it only showed the ESSID if I had in the correct name, when I put "network" or left it blank..it didnt find anything.
 How can I do a list scan like you said? Do I just do it at the terminal window. I'm really confused on how to make it connect to the internet if the ESSID is not filled in, or not correct.  


this is my /etc/network/interface configure

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp
wireless-essid wireless
wireless-key s:

auto eth0




iface wlan0 inet dhcp
wireless-essid misy5
wireless-key PASSWORD

auto wlan0



this is my /etc/iftab file

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.





Hope I can get it working. I know you are getting frustrated with me since I'm not used to linux.  Thanks again!:)

---

### Post by kevdog on 2007-07-24
Try this

Backup your /etc/network/interfaces file:
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

Ok now lets just edit you /etc/network/interfaces file
gksu gedit /etc/network/interfaces

Only have the following lines:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

Save the file and exit.

Then type:
sudo /etc/init.d/networking restart

Then go into 
System->Administration->Network
Select the wireless connection
Click on properties
Click on Enable Roaming

Should should be able to use the network-manager icon located by the clock to select your network automatically.

Do not select manual configuration because this will simply transpose what you just typed back into the interfaces file.
Just simply select the network, and then it should prompt you to enter the WEP key (note make sure you are using WEP and not WPA).

You are not using WPA are you??

---

### Post by 01queen on 2007-07-24
i do not see enable roaming all i see is enable connection. the network-manger icon. is it two computers?  I am using WEP not WPA.

---

### Post by kevdog on 2007-07-24
System->Administration->Network

I get a box labeled Network Settings

There are tabs for Connections,General,DNS,Hosts
 
In the Connections box I have a:
Wireless Connection
Modem Connection

Enable the Wireless Connection, click on the Properties box located on the right hand side,
with the new popup GUI, select Enable Roaming Mode.

If you have something else please post a screen capture.

---

### Post by 01queen on 2007-07-24
[IMG]http://img454.imageshack.us/img454/8872/propiv4.png[/IMG]


this is my properties.  I had to put in the user name and password so i could get on the internet.

---

### Post by kevdog on 2007-07-25
Here are my options -- they are in fact different:

---

### Post by 01queen on 2007-07-26
okay so i installed fiesty fawn, and got the card and everything installed.  the only problem is..my wireless card will not connect.  I can see the network and the name, but the things go around & around..no connection:(

---

### Post by 01queen on 2007-07-26
no wep or wpa

tried the command"sudo /etc/initt.d/dbus restart" it says command not found

i have restarted

i try the iwlists scan..it says command not found.

i have it enabled, i click on the computers and i see the ssid network name...but it wont connect.

---

### Post by kevdog on 2007-07-26
this is going to be the most painful step of the installation -- debugging

Check
```
ndiswrapper -v
ndiswrapper -l
lshw -C network
modinfo ndiswrapper
sudo modprobe -l ndiswrapper
ifconfig -a
```

Post 
```
/etc/iftab
/etc/network/interfaces
iwlist scan
```

I want you to type ```
dmesg | more
``` at command line, and look for any errors relating to the wireless card.

If everything is good, try to connect at command line
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed essid *ESSID_OF_ROUTER*
sudo dhclient wlan0
```

---

### Post by 01queen on 2007-07-26
okay..so I really am CONFUSED.. I did what you told me, and I'm going to post it below.  hope we can get it figured out..thanks:)


queen@queen:~$ cd ndiswrapper
queen@queen:~/ndiswrapper$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
queen@queen:~/ndiswrapper$ ndiswrapper -l
bcmwl5.sys : invalid driver!
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
queen@queen:~/ndiswrapper$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:70:4a:80:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=The Linksys Group, Inc.,02/14/2 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:14000000-14001fff irq:11

queen@queen:~/ndiswrapper$ modinfo ndiswrapper
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.38
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     BAC0B2B6ECA821BB17E1CCA
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)

queen@queen:~/ndiswrapper$ sudo moprobe -l ndiswrapper
Password:
sudo: moprobe: command not found


queen@queen:~/ndiswrapper$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1A:70:4A:80:82  
          inet6 addr: fe80::21a:70ff:fe4a:8082/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:345 (345.0 b)  TX bytes:468 (468.0 b)
          Interrupt:11 Memory:14000000-14002000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



/etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1a:70:4a:80:82 arp 1


/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback




queen@queen:~/ndiswrapper$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:90:4B:E1:BA:EA
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



I didnt see any errors whenever i typed in dmesg | more



this is what i get when i try to put eth0 down..

queen@queen:~/ndiswrapper$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

---

### Post by kevdog on 2007-07-27
The first thing you have to do is to reinstall the driver:
> queen@queen:~/ndiswrapper$ ndiswrapper -l
bcmwl5.sys : invalid driver!
lsbcmnds : driver installed

Do the following to remove the old drivers:
> cd /etc/ndiswrapper
sudo rm -R *

Then 
> ls -la
Make sure the directory is empty.

Next change into the directory where ever you have the windows drivers.
Try to reinstall:
> sudo ndiswrapper -i *****.inf  <---- Make sure .sys and .inf in same directory

Check to see if this went OK
> ndiswrapper -l

Next can you verify a few things:
Take your wireless card out and look on the back (or front):  Is this the MAC address of your card:
00:1a:70:4a:80:82

Please also list the following
/etc/modprobe.d/ndiswrapper
/etc/modules

---

### Post by 01queen on 2007-07-27
queen@queen:~/ndiswrapper$ ndiswrapper -l
bcmwl5.sys : invalid driver!
lsbcmnds : driver installed

even tho it says driver installed?  I still have to re do it?

---

### Post by 01queen on 2007-07-27
queen@queen:~/driver$ ndiswrapper -l
lsbcmnds : driver installed



i did the steps. it says driver installed

this is my /etc/modprobe.d/ndiswrapper

alias wlan0 ndiswrapper


i do not have a /etc/modules

---

### Post by 01queen on 2007-07-27
also. i can see the wireless name again and i click connect, and it keeps going around and around saying attempting to join the wireless network...

---

### Post by kevdog on 2007-07-27
Ok do the following (you are skipping a lot of steps)

```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Your /etc/modules file must have the statement ndiswrapper.

Edit the /etc/iftab file:
```
gksu gedit /etc/iftab

Change eth0 to wlan0
```

Save the file and exit

Reboot
```
sudo shutdown -r now
```

---

### Post by 01queen on 2007-07-27
okay i did that, i still getting "atempting to join the wireless network "wireless"" but no connection...

I still don't have a "/etc/modules"

---

### Post by kevdog on 2007-07-28
Do the following:

```
sudo touch /etc/modules
sudo chmod +644 /etc/modules
echo ndiswrapper | sudo tee -a /etc/modules
```

Then
```
sudo shutdown -r now
```

---

### Post by 01queen on 2007-07-28
when i try to do the chmod i get 'chmod: invallid mode: '+644'

also when I do the shutdown -r command. it always hangs when it's telling me the brand of computer i have, and I just press the power button again, do you think that is messing up what I put in earlier? 

but either way I still click on it to try to get to my network, and it still goes around & around --> attemping to connect... nothing still:(

---

### Post by kevdog on 2007-07-28
Sorry try the following then:

```
sudo chmod 644 /etc/modules
```

---

### Post by 01queen on 2007-07-28
do I need to do 

sudo touch /etc/modules
sudo chmod 644 /etc/modules
echo ndiswrapper | sudo tee -a /etc/modules



like that? and then restart? in that order?

---

### Post by kevdog on 2007-07-28
Yes, and you can restart your machine anyway you like, use the GUI or the menus to restart if you want.

---

### Post by 01queen on 2007-07-29
k i did that. still nothing..i can see the wireless name..but it wont connect..

---

### Post by kevdog on 2007-07-29
Lets check everything out again since the last time there were problems we found:
```
ndiswrapper -v
ndiswrapper -l
lshw -C network
modinfo ndiswrapper
sudo modprobe -l ndiswrapper
ifconfig -a

```

Post the following also:

```
/etc/iftab
/etc/network/interfaces
iwlist scan
```

---

### Post by 01queen on 2007-07-29
queen@queen:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
queen@queen:~$ ndiswrapper -l
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
queen@queen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:70:4a:80:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=The Linksys Group, Inc.,02/14/2 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:1c000000-1c001fff irq:11
queen@queen:~$ modinfo ndiswrapper
modinfo: could not open ndiswrapper: No such device
queen@queen:~$ sudo modprobe -l ndiswrapper
Password:
/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
queen@queen:~$ ifconfig -a
irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:70:4A:80:82  
          inet6 addr: fe80::21a:70ff:fe4a:8082/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:486 (486.0 b)  TX bytes:468 (468.0 b)
          Interrupt:11 Memory:1c000000-1c002000 


/etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:1a:70:4a:80:82 arp 1


/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iwlist scan

queen@queen:~$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:E1:BA:EA
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by kevdog on 2007-07-29
Please make sure that your router has encryption (WEP/WPA) turned off (it seems that it is), and MAC filtering turned off.

One thing you gave me seems really strange:
> queen@queen:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

I dont know what to make of this statement.  Its really strange.  How did you install ndiswrapper?? Did you compile from source, and if so, what version did you download??

Have you blacklisted bcm43xxx in the /etc/modprobe.d/blacklist file?

In the meantime what response do you get if you type the following:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid wireless
sudo dhclient wlan0
```

---

### Post by 01queen on 2007-07-29
i was thinking the same thing about the ndiswrapper statement. i installed it the same way i did the first time. the actual file does say ndiswrapper 1-4.7, wep key and mac filtering is off.


when i do sudo dhclient wlan0 i get

Internet systems consortium DHCP client v3.0.4
copyright 2004-2006 Internet system consortium.
All right reservered.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:70:4a:80:82
sending on  LPF/wlan0/00:1a:70:4a:80:82
Sending on socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 38101 seconds


when i hover over the computers, i have to click enable networking, and then i see the essid wireless name "wireless" and click it and it's still going around and around?  

That's whas confuses me..I can see the network, but I can't connect to it...

you think we should just start over & do it again?  when I installed ndiswrapper, I have my wireless card in I believe, I only put the PCI card w/ the wire whenever i downloaded ndiswrapper... should i do everything w/ the wireless card in..and no hard wire to the laptop?  this is getting really frustrating!

I can see my host name(linux box) on the routing monitor(xp comp)



I can connect to the wireless router whenever i put the essid name in manually..but not when it's on enable roaming...if that helps anythine

---

### Post by kevdog on 2007-07-29
Hold on for a minute:

I saw the following:
> when i do sudo dhclient wlan0 i get

Internet systems consortium DHCP client v3.0.4
copyright 2004-2006 Internet system consortium.
All right reservered.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1a:70:4a:80:82
sending on LPF/wlan0/00:1a:70:4a:80:82
Sending on socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 38101 seconds

This tells me that you just received an local area internet address of 192.168.2.2.  You ARE connected to the router!!! (via a manual approach).  You should at this point be able to open firefox and browse the web.  Forget network manager for the moment, can you browse the internet??  You should be able to do:
> ifconfig -a

And see wlan0 with an internet address of 192.168.2.2

---

### Post by 01queen on 2007-07-29
i can connect after that, but isnt that just putting in the essid manually like I did w/ the GUI?  wlan0 ipaddy is 192.168.2.2 and I can access the internet, but that's manually putting it in correct?

because when I say sudo iwconfig wlan0 essid wireless

that is my essid name

---

### Post by kevdog on 2007-07-29
Now that you can connect to the internet, we have so more flexibility.  First I want you to upgrade your system

sudo aptitude update && sudo aptitude upgrade

Once done, I want you to install the svn package

sudo aptitude install subversion

Once installed I want you to download the svn version of ndiswrapper:
cd ~
svn co [https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper](https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper) ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make

Before installing, let me know if you are getting any errors -- basically we are going to install the cutting edge version of svn.  Im currently getting revision 2433 as the current svn version of ndiswrapper.  Ive personally verified that it does compile without errors!!!

---

### Post by 01queen on 2007-07-29
okay so i get everything going good. until i get to make distclean..i get 
make: *** No rule to make target 'distclean'.  Stop.

once you repost, i will try whatever you say in the morning & reply:) thanks so much for all your help.

---

### Post by kevdog on 2007-07-29
Can you list the directory contents of ~/ndiswrapper_svn??

---

### Post by 01queen on 2007-07-30
branches, tags, trunk

also what i did in the terminal window, is gone when i restart.

---

### Post by kevdog on 2007-07-30
I know you will have to retype the commands the best thing I would tell you for now is since we are trying to get this thing automated -- (it works but will not automate) is to stick those commands in a file to make a script file like this:

Open the editor:
```
gedit ~/network
```

```
#!/bin/bash
*Put the commands here from previous post, ie sudo ifconfig wlan0 down, etc*
```


Save file and exit.  Make the file executable:
```
chmod 744 ~/network
```

Then when you reboot and want to start the network, do the following for now:
```
./network
```

Ok lets retry to grab the svn (I may have given you the wrong address)
```
rm -R ~/ndiswrapper_svn/* <----This deletes everything in the directory
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ~/ndiswrapper_svn
cd ~/ndiswrapper_svn
svn up
make distclean
make
```

Also make sure your router is broadcasting its ESSID.  There should be a setting that allows it to broadcast.

---

### Post by 01queen on 2007-07-30
when i try to do the rm -R command. it gives me stuff where I have to keep clicking enter for it to delete, and then after i keep clicking enter and i get back to a prompt...i try the 
svn co [https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper](https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper) ~/ndiswrapper_svn


it says svn co [https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper](https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper) ~/ndiswrapper_svn svn: '/home/queen/ndiswrapper_svn' is already a working copy for a different url

---

### Post by kevdog on 2007-07-30
First time Ive seen that message.  Im no svn expert

```
cd ~/ndiswrapper_svn
rm -rf *
rm -rf *.svn

```
Do an
```
ls -la
```
Make sure the directory is empty

```
cd ~
```
Then checkout the module as instructed before:
```
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ~/ndiswrapper_svn
cd ~/ndiswrapper_svn
svn up
make distclean
make
```

Sorry about the confusion.  Some of the problems you've presented to me I haven't seen before!  We are both learning

---

### Post by 01queen on 2007-07-30
okay got that done. no errors:) now what? --i rebooted..no internet..
yes we both are learning:)

just wondering. if you know, everytime after I do the shutdown -r or whatever..it always freezes up like at the IBM thinkpad screen. any ideas? but once I click the power button & do it the other way. it's fine..

---

### Post by kevdog on 2007-07-30
Again you can shutdown or reboot anyway you like -- like using the button next to the clock if you want.  As far as your problem with the computer not going anywhere during shutdown, I too have had that problem periodically.  I havent had it in about 2 months but who the heck knows???
Its probably related to the ACPCI or the package controlling battery usage and power for the laptops.  I know they have had problems with this particular module for sometime.

Anyway

Great everything is working up to this point.
Now we need to uninstall the previous ndiswrapper package

If I remember the directories correctly

```
cd ~/ndiswrapper
sudo rmmod ndiswrapper
sudo ndiswraper *driver_name <--- name of driver **without **.inf extension -- use ndiswrapper -l to discover name if you forgot*
sudo make uninstall
```

Then do a 
```
sudo updatedb <---- This will take a while to run
```

Then search for 3 files and make sure they dont show up
```
locate ndiswrapper
locate loadndisdriver
locate ndiswrapper.ko
```

If the 3 above locate statements show anything, please post and do not proceed.

```
Then cd ~/ndiswrapper_svn
sudo make install
```

Then do as previously directed (these commands should be old hat)
sudo ndiswrapper *****.inf
sudo depmod -a
sudo modprobe ndiswrapper


Again I didnt list any of the verification steps above. Make sure your router is broadcasting its ESSID!!!

---

### Post by 01queen on 2007-07-31
this is what i get when i do the sudo ndiswrapper driver_name

queen@queen:~/ndiswrapper$ sudo ndiswrapper LSBCMNDS
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information



in my router, there is a part that says "Hid my wireless network" I have NO checked. that's the same thing as broadcasting correct?  Other windows laptops can connect to my network at home, without anything being set up.

---

### Post by kevdog on 2007-07-31
Go back to the original guide

sudo ndiswrapper -i *******.inf <---Put name of .inf file here along with .sys file in same directory

---

### Post by 01queen on 2007-07-31
queen@queen:~/ndiswrapper$ sudo ndiswrapper -i LSBCMNDS.inf
Password:
driver lsbcmnds is already installed
queen@queen:~/ndiswrapper$ sudo ndiswrapper bcmwl5.sys
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card



is that correct?

---

### Post by kevdog on 2007-07-31
See if the driver might be installed, it might be:

ndiswrapper -l

If only one driver is listed you are good to go..

sudo depmod -a
sudo modprobe ndiswrapper

---

### Post by 01queen on 2007-07-31
okay yea just one dirver is installed. i then did the sudo depmod -a and sudo modprobe ndiswarpper

now...?

---

### Post by kevdog on 2007-07-31
Make sure you have the following files and contents
/etc/modprobe.d/ndiswrapper
    Inside file should be something like alias wlan0 ndiswrapper

/etc/modules
   Make sure inside the file there is a line that says ndiswrapper

/etc/network/interfaces
   Make sure the only lines in the file are the following:
auto lo
iface lo inet loopback

Make sure inside network manager, roaming mode is enabled

Thats it, reboot and what happens

---

### Post by 01queen on 2007-07-31
inside modules there are about 4 lines that says ndiswrapper--that okay?

everything else just like you said. i restart with my wireless card in the slot...and.....gui says no connection--i click firefox(just in case I do have connect)---no internet..i click to connect to 'wireless' network..ATTEMPTING to connect still-->still nothing=(

I have 2 slots on the side of my laptop..I tired both of them...not sure why it wont connection..everything looks right

---

### Post by kevdog on 2007-07-31
Remove the 3 extra lines inside /etc/modules

Because we updated the driver, can you connect manually by typing the commands at the command line as before?  I just want to make sure the driver is actually working (like before!!).  I dont remember the exact commands, but they were listed previously.

---

### Post by 01queen on 2007-07-31
i can not remove the extra lines..it is a read only version. how do I make it where I can...

i can connect after i do the wlan0 down..up..managed..mode..all that jazz
even tho the GUI says it's d/c

---

### Post by kevdog on 2007-07-31
To make the file writeable

sudo chmod 644 /etc/modules
gksu gedit /etc/modules

Delete the extra lines

So all this work and still network manager just sits there!  Sucks!!! I know the driver is working since you do it manually.  You not hiding you essid.  Let me get back to you, I have to look a few things up about network manager.

---

### Post by 01queen on 2007-07-31
if I was hiding my essid, it wouldnt even show it under the connections as wireless would it?  also other people are able to connect..so everything with broadcasting is fine correct?

got all the other lines deleted. thanks for all your help. i also messaged linksys about it..not sure of how much help they will be haha

---

### Post by kevdog on 2007-07-31
No, it could still see it if it were hidden (that's the fallacy behind it).  Its just that sometimes there is a driver problem and conflict with nwmanager.  If I knew the exact nature of it, I could tell you!

---

### Post by kevdog on 2007-07-31
Can you post the following:

ndiswrapper -l
modinfo ndiswrapper 
iwlist scan
lshw -C network

Im about to bail on networkmanager and go with wicd.

---

### Post by 01queen on 2007-07-31
queen@queen:~$ ndiswrapper -l
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
queen@queen:~$ modinfo ndiswrapper
modinfo: could not open ndiswrapper: No such device
queen@queen:~$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:E1:BA:EA
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

queen@queen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:70:4a:80:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=The Linksys Group, Inc.,02/14/2 ip=192.168.2.2 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:14000000-14001fff irq:11
queen@queen:~$

whatever makes it easy to work & do is fine with me!:)

---

### Post by kevdog on 2007-07-31
One last thing:

ndiswrapper -v 
sudo modinfo ndiswrapper

---

### Post by 01queen on 2007-07-31
queen@queen:~$ cd ndiswrapper
queen@queen:~/ndiswrapper$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)


queen@queen:~/ndiswrapper$ sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.38
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     BAC0B2B6ECA821BB17E1CCA
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)




it's still showing as 1.38. but the file says 1.47. i'm confused

---

### Post by kevdog on 2007-07-31
I dont think the old version was completely removed somehow.  I want you to uninstall everything again and review the old posts.  Perhaps when done uninstalling you can do a ndiswrapper -v statement to ensure nothing comes up to prove it is uninstalled.  Also I want you to read this post on the uninstallation of ndiswrapper.  Many of the commands listed in the post will need to be prefaced with sudo.  

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

### Post by 01queen on 2007-08-01
i'm really confused. when i try the 
sudo modprobe -r ndiswrapper
it ask for the password and then i put it in...

then it took  me back to the prompt.

i then try: You need to remove the user space tools ndiswrapper (in
/usr/sbin) and loadndisdriver (in /sbin), and kernel module ndiswrapper (in /lib/modules/`uname -r`/misc). 


well I try it the GUI and it will not delete cuz of rights, i go to /usr/sbin in the terminal and type in modprobe -r ndiswrapper

wouldnt that delete that ndiswrapper in that directory?



also..refering to the previous post..do you want me to uninstall ndiswrapper or ndiswrapper_SVN?

---

### Post by kevdog on 2007-08-01
Try the following *with an internet connection*

```
cd ~/ndiswrapper_svn
svn up
make distclean
make

```

```
cd ~/ndiswrapper
sudo make uninstall
```

Then the following

```
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko
```

Then I want you to do
```
sudo updatedb
```
Then 
```
locate ndiswrapper
```

There will be a bunch of things listed, but I dont want anything in directories starting with /usr/

Then
```
locate loadndisdriver
```

Again make sure nothing that is listed begins with the directory /sbin

Then 
```
locate ndiswrapper.ko
```

Again make sure nothing that is listed begins with the directory /lib/modules

---

### Post by 01queen on 2007-08-01
when i do 
cd ~/ndiswrapper: sudo make uninstall

I get make: *** No rule to make target 'uninstall'.  Stop.

---

### Post by kevdog on 2007-08-01
Good, just keep going!!

Also, before proceeding to the next step:

cd ~/ndiswrapper_svn
sudo make uninstall

---

### Post by 01queen on 2007-08-01
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

all of them said cannot remove..no such file or directory..


this is what it shows when i do: locate ndiswrapper


queen@queen:~/ndiswrapper_svn$ locate ndiswrapper
/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper
/usr/src/linux-headers-2.6.20-15-generic/include/config/ndiswrapper.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ndiswrapper
/usr/src/linux-headers-2.6.20-15-generic/include/config/ndiswrapper/wq.h
/usr/src/linux-headers-2.6.20-15/ubuntu/misc/ndiswrapper
/usr/src/linux-headers-2.6.20-15/ubuntu/misc/ndiswrapper/Makefile
/usr/share/man/man8/ndiswrapper.8
/home/queen/ndiswrapper_svn
/home/queen/ndiswrapper_svn/driver
/home/queen/ndiswrapper_svn/driver/usb.h
/home/queen/ndiswrapper_svn/driver/pnp.h
/home/queen/ndiswrapper_svn/driver/wrapper.c
/home/queen/ndiswrapper_svn/driver/ntoskernel_io.c
/home/queen/ndiswrapper_svn/driver/.ntoskernel.o.cmd
/home/queen/ndiswrapper_svn/driver/wrapndis.c
/home/queen/ndiswrapper_svn/driver/iw_ndis.h
/home/queen/ndiswrapper_svn/driver/usb.o
/home/queen/ndiswrapper_svn/driver/ntoskernel.o
/home/queen/ndiswrapper_svn/driver/divdi3.c
/home/queen/ndiswrapper_svn/driver/iw_ndis.c
/home/queen/ndiswrapper_svn/driver/wrapper.o
/home/queen/ndiswrapper_svn/driver/winnt_types.h
/home/queen/ndiswrapper_svn/driver/.svn
/home/queen/ndiswrapper_svn/driver/.svn/entries
/home/queen/ndiswrapper_svn/driver/.svn/format
/home/queen/ndiswrapper_svn/driver/.svn/all-wcprops
/home/queen/ndiswrapper_svn/driver/.svn/tmp
/home/queen/ndiswrapper_svn/driver/.svn/tmp/props
/home/queen/ndiswrapper_svn/driver/.svn/tmp/prop-base
/home/queen/ndiswrapper_svn/driver/.svn/tmp/text-base
/home/queen/ndiswrapper_svn/driver/.svn/props
/home/queen/ndiswrapper_svn/driver/.svn/prop-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/wrapper.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/usb.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/wrapndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/wrapper.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ntoskernel_io.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/hal.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/pe_linker.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/loader.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/iw_ndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/proc.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/iw_ndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/usb.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/longlong.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/pnp.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/winnt_types.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/pe_linker.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/wrapndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/loader.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ntoskernel.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/pnp.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ndiswrapper.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/ntoskernel.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/prop-base/divdi3.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/workqueue.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapper.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/usb.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapper.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ntoskernel_io.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/hal.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapmem.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/pe_linker.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapmem.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/loader.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/iw_ndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/lin2win.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/proc.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/iw_ndis.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/usb.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/longlong.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/pnp.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/winnt_types.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/pe_linker.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/wrapndis.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/loader.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ntoskernel.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/win2lin_stubs.S.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/crt.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/pnp.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ndiswrapper.h.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/ntoskernel.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/divdi3.c.svn-base
/home/queen/ndiswrapper_svn/driver/.svn/text-base/rtl.c.svn-base
/home/queen/ndiswrapper_svn/driver/crt.c
/home/queen/ndiswrapper_svn/driver/proc.o
/home/queen/ndiswrapper_svn/driver/loader.o
/home/queen/ndiswrapper_svn/driver/wrapndis.o
/home/queen/ndiswrapper_svn/driver/wrapmem.c
/home/queen/ndiswrapper_svn/driver/.divdi3.o.cmd
/home/queen/ndiswrapper_svn/driver/ndis_exports.h
/home/queen/ndiswrapper_svn/driver/ndis.o
/home/queen/ndiswrapper_svn/driver/rtl_exports.h
/home/queen/ndiswrapper_svn/driver/.ndiswrapper.ko.cmd
/home/queen/ndiswrapper_svn/driver/.ntoskernel_io.o.cmd
/home/queen/ndiswrapper_svn/driver/rtl.c
/home/queen/ndiswrapper_svn/driver/loader.h
/home/queen/ndiswrapper_svn/driver/wrapper.h
/home/queen/ndiswrapper_svn/driver/pe_linker.c
/home/queen/ndiswrapper_svn/driver/hal.o
/home/queen/ndiswrapper_svn/driver/.iw_ndis.o.cmd
/home/queen/ndiswrapper_svn/driver/pe_linker.h
/home/queen/ndiswrapper_svn/driver/.wrapper.o.cmd
/home/queen/ndiswrapper_svn/driver/pnp.c
/home/queen/ndiswrapper_svn/driver/Module.symvers
/home/queen/ndiswrapper_svn/driver/ndiswrapper.ko
/home/queen/ndiswrapper_svn/driver/loader.c
/home/queen/ndiswrapper_svn/driver/.pe_linker.o.cmd
/home/queen/ndiswrapper_svn/driver/ndiswrapper.h
/home/queen/ndiswrapper_svn/driver/iw_ndis.o
/home/queen/ndiswrapper_svn/driver/.loader.o.cmd
/home/queen/ndiswrapper_svn/driver/win2lin_stubs.S
/home/queen/ndiswrapper_svn/driver/ntoskernel_io_exports.h
/home/queen/ndiswrapper_svn/driver/pe_linker.o
/home/queen/ndiswrapper_svn/driver/usb_exports.h
/home/queen/ndiswrapper_svn/driver/.usb.o.cmd
/home/queen/ndiswrapper_svn/driver/ndiswrapper.mod.o
/home/queen/ndiswrapper_svn/driver/.ndis.o.cmd
/home/queen/ndiswrapper_svn/driver/.wrapndis.o.cmd
/home/queen/ndiswrapper_svn/driver/longlong.h
/home/queen/ndiswrapper_svn/driver/.wrapmem.o.cmd
/home/queen/ndiswrapper_svn/driver/.built-in.o.cmd
/home/queen/ndiswrapper_svn/driver/divdi3.o
/home/queen/ndiswrapper_svn/driver/.ndiswrapper.o.cmd
/home/queen/ndiswrapper_svn/driver/wrapmem.h
/home/queen/ndiswrapper_svn/driver/crt_exports.h
/home/queen/ndiswrapper_svn/driver/.rtl.o.cmd
/home/queen/ndiswrapper_svn/driver/.ndiswrapper.mod.o.cmd
/home/queen/ndiswrapper_svn/driver/.tmp_versions
/home/queen/ndiswrapper_svn/driver/.tmp_versions/ndiswrapper.mod
/home/queen/ndiswrapper_svn/driver/ndiswrapper.o
/home/queen/ndiswrapper_svn/driver/wrapmem.o
/home/queen/ndiswrapper_svn/driver/ndis.h
/home/queen/ndiswrapper_svn/driver/ndiswrapper.mod.c
/home/queen/ndiswrapper_svn/driver/crt.o
/home/queen/ndiswrapper_svn/driver/ntoskernel_io.o
/home/queen/ndiswrapper_svn/driver/ntoskernel_exports.h
/home/queen/ndiswrapper_svn/driver/wrapndis.h
/home/queen/ndiswrapper_svn/driver/Makefile
/home/queen/ndiswrapper_svn/driver/lin2win.h
/home/queen/ndiswrapper_svn/driver/.crt.o.cmd
/home/queen/ndiswrapper_svn/driver/pnp.o
/home/queen/ndiswrapper_svn/driver/hal.c
/home/queen/ndiswrapper_svn/driver/workqueue.c
/home/queen/ndiswrapper_svn/driver/.pnp.o.cmd
/home/queen/ndiswrapper_svn/driver/hal_exports.h
/home/queen/ndiswrapper_svn/driver/proc.c
/home/queen/ndiswrapper_svn/driver/.hal.o.cmd
/home/queen/ndiswrapper_svn/driver/ntoskernel.h
/home/queen/ndiswrapper_svn/driver/usb.c
/home/queen/ndiswrapper_svn/driver/rtl.o
/home/queen/ndiswrapper_svn/driver/ntoskernel.c
/home/queen/ndiswrapper_svn/driver/built-in.o
/home/queen/ndiswrapper_svn/driver/compat.h
/home/queen/ndiswrapper_svn/driver/ndis.c
/home/queen/ndiswrapper_svn/driver/.proc.o.cmd
/home/queen/ndiswrapper_svn/.svn
/home/queen/ndiswrapper_svn/.svn/entries
/home/queen/ndiswrapper_svn/.svn/format
/home/queen/ndiswrapper_svn/.svn/all-wcprops
/home/queen/ndiswrapper_svn/.svn/tmp
/home/queen/ndiswrapper_svn/.svn/tmp/props
/home/queen/ndiswrapper_svn/.svn/tmp/prop-base
/home/queen/ndiswrapper_svn/.svn/tmp/text-base
/home/queen/ndiswrapper_svn/.svn/props
/home/queen/ndiswrapper_svn/.svn/prop-base
/home/queen/ndiswrapper_svn/.svn/prop-base/INSTALL.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/ndiswrapper.spec.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/ndiswrapper.8.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/README.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/AUTHORS.svn-base
/home/queen/ndiswrapper_svn/.svn/prop-base/ChangeLog.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base
/home/queen/ndiswrapper_svn/.svn/text-base/INSTALL.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/ndiswrapper.spec.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/ndiswrapper.8.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/README.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/AUTHORS.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/ChangeLog.svn-base
/home/queen/ndiswrapper_svn/.svn/text-base/loadndisdriver.8.svn-base
/home/queen/ndiswrapper_svn/ChangeLog
/home/queen/ndiswrapper_svn/utils
/home/queen/ndiswrapper_svn/utils/ndiswrapper-buginfo
/home/queen/ndiswrapper_svn/utils/.svn
/home/queen/ndiswrapper_svn/utils/.svn/entries
/home/queen/ndiswrapper_svn/utils/.svn/format
/home/queen/ndiswrapper_svn/utils/.svn/all-wcprops
/home/queen/ndiswrapper_svn/utils/.svn/tmp
/home/queen/ndiswrapper_svn/utils/.svn/tmp/props
/home/queen/ndiswrapper_svn/utils/.svn/tmp/prop-base
/home/queen/ndiswrapper_svn/utils/.svn/tmp/text-base
/home/queen/ndiswrapper_svn/utils/.svn/props
/home/queen/ndiswrapper_svn/utils/.svn/prop-base
/home/queen/ndiswrapper_svn/utils/.svn/prop-base/ndiswrapper-buginfo.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/prop-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/prop-base/loadndisdriver.c.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/prop-base/ndiswrapper.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/text-base
/home/queen/ndiswrapper_svn/utils/.svn/text-base/ndiswrapper-buginfo.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/text-base/Makefile.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/text-base/loadndisdriver.c.svn-base
/home/queen/ndiswrapper_svn/utils/.svn/text-base/ndiswrapper.svn-base
/home/queen/ndiswrapper_svn/utils/loadndisdriver.c
/home/queen/ndiswrapper_svn/utils/loadndisdriver
/home/queen/ndiswrapper_svn/utils/Makefile
/home/queen/ndiswrapper_svn/utils/ndiswrapper
/home/queen/ndiswrapper_svn/README
/home/queen/ndiswrapper_svn/INSTALL
/home/queen/ndiswrapper_svn/loadndisdriver.8
/home/queen/ndiswrapper_svn/ndiswrapper.spec
/home/queen/ndiswrapper_svn/AUTHORS
/home/queen/ndiswrapper_svn/Makefile
/home/queen/ndiswrapper_svn/ndiswrapper.8
/home/queen/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fqueen%2Fndiswrapper.xml
/home/queen/ndiswrapper
/home/queen/ndiswrapper/ndiswrapper-1.47.tar.gz
/home/queen/ndiswrapper/ndiswrapper-1.47
/home/queen/ndiswrapper/ndiswrapper-1.47/driver
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/usb.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pnp.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapper.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel_io.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ntoskernel.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapndis.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/iw_ndis.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/usb.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/divdi3.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/iw_ndis.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapper.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/winnt_types.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/crt.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/proc.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/loader.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapndis.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapmem.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.divdi3.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndis_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndis.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/rtl_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ndiswrapper.ko.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ntoskernel_io.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/rtl.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/loader.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pe_linker.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/hal.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.iw_ndis.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pe_linker.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.wrapper.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pnp.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/Module.symvers
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndiswrapper.ko
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/loader.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.pe_linker.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndiswrapper.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/iw_ndis.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.loader.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/win2lin_stubs.S
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel_io_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pe_linker.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/usb_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.usb.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndiswrapper.mod.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ndis.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.wrapndis.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/longlong.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.wrapmem.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.built-in.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/divdi3.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ndiswrapper.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapmem.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/crt_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.rtl.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.ndiswrapper.mod.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndiswrapper.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapmem.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndis.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndiswrapper.mod.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/crt.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel_io.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/wrapndis.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/Makefile
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/lin2win.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.crt.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/pnp.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/hal.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/workqueue.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.pnp.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/hal_exports.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/proc.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.hal.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/usb.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/rtl.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ntoskernel.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/built-in.o
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/compat.h
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/ndis.c
/home/queen/ndiswrapper/ndiswrapper-1.47/driver/.proc.o.cmd
/home/queen/ndiswrapper/ndiswrapper-1.47/ChangeLog
/home/queen/ndiswrapper/ndiswrapper-1.47/utils
/home/queen/ndiswrapper/ndiswrapper-1.47/utils/ndiswrapper-buginfo
/home/queen/ndiswrapper/ndiswrapper-1.47/utils/loadndisdriver.c
/home/queen/ndiswrapper/ndiswrapper-1.47/utils/loadndisdriver
/home/queen/ndiswrapper/ndiswrapper-1.47/utils/Makefile
/home/queen/ndiswrapper/ndiswrapper-1.47/utils/ndiswrapper
/home/queen/ndiswrapper/ndiswrapper-1.47/README
/home/queen/ndiswrapper/ndiswrapper-1.47/INSTALL
/home/queen/ndiswrapper/ndiswrapper-1.47/loadndisdriver.8
/home/queen/ndiswrapper/ndiswrapper-1.47/ndiswrapper.spec
/home/queen/ndiswrapper/ndiswrapper-1.47/AUTHORS
/home/queen/ndiswrapper/ndiswrapper-1.47/Makefile
/home/queen/ndiswrapper/ndiswrapper-1.47/ndiswrapper.8
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper
/etc/ndiswrapper/lsbcmnds
/etc/ndiswrapper/lsbcmnds/14E4:4318:0048:1737.5.conf
/etc/ndiswrapper/lsbcmnds/14E4:4318.5.conf
/etc/ndiswrapper/lsbcmnds/14E4:4320:0049:1737.5.conf
/etc/ndiswrapper/lsbcmnds/lsbcmnds.inf
/etc/ndiswrapper/lsbcmnds/14E4:4320.5.conf
/etc/ndiswrapper/lsbcmnds/14E4:4320:4320:1737.5.conf
/etc/ndiswrapper/lsbcmnds/bcmwl5.sys






when i do locate loadndisdriver it does not have anything with /sbin

and the same with locate ndiswrapper.ko nothing being in the /lob/modules

---

### Post by kevdog on 2007-08-01
Good

That is what I was hoping for.
Everything is OK.

Now a couple more commands (some may not work)
```
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper 
```


Make sure the /etc/ndiswrapper directory is empty

Thanks -- just about to reinstall ndiswrapper

You can also do the following:
```
cd ~/ndiswrapper_svn
make distclean
make
```

---

### Post by 01queen on 2007-08-01
there is no /etc/ndiswrapper

but i did the 

cd ~/ndiswrapper_svn
make distclean
make



everything went okay:)

---

### Post by kevdog on 2007-08-01
Ok

```
cd ~/ndiswrapper_svn
sudo make install
```

Then post the following
```
ndiswrapper -v
```

---

### Post by 01queen on 2007-08-01
now the version is saying version 1.48rcl

but it says you must re-install the drivers if they were installed before..



so we are getting better now right?

also if someone can connect to my network w/o knowing the essid name..then it's broadcast right?

---

### Post by kevdog on 2007-08-01
Wow better than 1.47 -- good, I havent used this version yet.

OK
```
sudo ndiswrapper -i *****.inf <---- with .sys file in same directory
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

Ensure only one entry of ndiswrapper in the /etc/modules file.

Reboot!

Bring network up manually (down, up, etc)

Post the following
> modinfo ndiswrapper
sudo modprobe -l ndiswrapper

---

### Post by 01queen on 2007-08-01
i do 
sudo ndiswrapper -i LSBCMNDS.inf 


and it says driver already installed..

I then: cd ~/ndiswrapper
and do sudo modprobe ndiswrapper


and sudo ndiswrapper -m
and it says module configuration already contains alias directive

there is only one entry of ndiswrapper in the /etc/modules file..

i reboot w/ the wireless card in...and......
when i click on the two little computers..it says no network devices have been found...

---

### Post by kevdog on 2007-08-01
Reinstall drivers

cd /etc/ndiswrapper
sudo rm -R *

Make sure directory is empty by using **ls** command and making sure nothing shows

Then:
sudo rmmod ndiswrapper
sudo ndiswrapper -i *****.inf <---- with .sys file in same directory
sudo depmod -a
sudo modprobe ndiswrapper

**Bring up network manually** as you did before to get it to work

---

### Post by 01queen on 2007-08-01
when i do ls
it takes it back to the queen@queen: /etc/ndiswrapper$ 
prompt..

also when I do the sudo rmmod ndiswrapper am I suppose to do that in the /etc/ndiswrapper prompt?  if so it went through but when I do the install the driver..
it says installing lsbcmnds...
couldn't open LSBCMNDS.inf:  no such file or directory at /usr/sbin/ndiswrapper line 217

I went back to the reg. prompt just queen@queen: and did sudo ndiswrapper -i LSBCMNDS.inf and it says it's already installed...

now when I go to the network manager...it doesnt show the card...it just shows the modem=( not good

---

### Post by kevdog on 2007-08-01
Im really starting to get frustrated..This is like the 4th time weve done this.  Yes Im skipping some things but I thought you would know how to do it by now since weve gone through it sooo many times:

Here is a clarification

Before installing drivers into ndiswrapper, make sure no other bad or duplicate drivers are installed.  To do this 
```
cd /etc/ndiswrapper
ls -la
```

If the directory is empty other than . and .., then nothing is installed. If anything else is listed you need to totally clear out the directory with
```
sudo rm -R *
```

Ok next step

```
cd ~
sudo rmmod ndiswrapper
```

```
cd *to whatever directory the *.inf and *.sys files are located in*
```  
The *.inf and *.sys files are the WinXP drivers.

```
sudo ndiswrapper -i *****.inf <---- with .sys file in same directory
sudo depmod -a
sudo modprobe ndiswrapper

```

---

### Post by 01queen on 2007-08-01
okay. i clicked on the little thing to connect to wireless...and it actually connects that way..

i'm just wondering what we did wrong the first time for it not to work. 
sorry i'm so "blonde" sometimes all these steps just look like a bunch of jumble to me!!

if I want to do this again. or if I need to help someone...basically the last 2 or 3 pages where I need to start right?



thanks for the help tho. sorry I'm so confusing/frustrating(making you)


I am going to take the laptop in a few mins to my friends house just to make sure it'll connect to other networks....

---

### Post by kevdog on 2007-08-01
Congratulations (if you are not joking with me).  Only thing I can figure is that v1.38 doesnt work well with network manager.  I'll post the instructions again, however you need to remember you didnt something very diferent in this thread that no one I have helped before has done -- install ndiswrapper from svn, which requires an internet connection.

If you dont have an internet connection then you need to download source packages, however in this case that didnt really work well.

My "universal instructions" are included below, however it doesnt contain any info about removing ndiswrapper or subsequently using svn to download the cutting edge package.  I probably should rewrite these instructions to include this info.

Anyway, good luck, if you need anymore help with things (ie WEP/WPA) let me know!!



------

Here are my "universal installation instructions" for ndiswrapper:

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.

---

### Post by 01queen on 2007-08-01
yea it's working seriously. ha. thank you so much for your help.  I can always have some kindof connection because I can wire it up, which works better.

If I need to do the wep key, something should pop up and ask me for the password right?-------yea something pops up..i tested it out:) i got it connect w/ a WEP key. man you are a genius!! thanks so much!!!

there is something where we have to put in bcm4xx right? where would that fit into the instructions?

---

### Post by kevdog on 2007-08-01
I guess that could go after the last command listed above:

If using a device with a broadcom chipset, please perform the following:
```

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by 01queen on 2007-08-01
true. well i got it up & running....I went to my friends..it connected fine:) it prompted me for the key. and I put it in and I was good to go. THANK YOU TIMES A MILLION!!!

---

