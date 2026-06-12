---
title: "trouble with ndiswrapper"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by Chet Hardin on 2007-06-04
Hey. I get my wifi card to work. Then I shut down and when I restart, the card doesn't work anymore. 

Now, I have been having trouble running the ndiswrapper driver installation tool. Every time I try to launch the applet, it fails. So I went into the terminal and came back with this.

chet@chet-laptop:~$ gksu /usr/bin/ndisgtk
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]   # strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'

Does this have anything to do with my troubles?

Thanks.

---

### Post by kevdog on 2007-06-05
Once you get it installed, working, and everything is *HOAKY* did you type:
ndiswrapper -m 
so that the module is loaded by default at runtime???

This command add a file found at:
/etc/modprobe.d/ndiswrapper

Open this file and make sure the name of the interface is correct.  It always installs it with wlan0 and you may be using eth0 or some other interace name.  If it is incorrect, edit the file with sudo and change wlan0 to the appropriate interface.

---

### Post by Chet Hardin on 2007-06-05
Hey Kevdog, thanks for the reply. Could someone walk me through the process of editing the ndiswrapper file?

Thanks.

Chet

---

### Post by kevdog on 2007-06-05
Could you be more specific - Ive never had to edit ndiswrapper.

---

### Post by Chet Hardin on 2007-06-05
Kevdog. You were right. The file ndiswrapper in modprobe.d doesn't match the interface I am using. So I need to edit the file. But I have never edited a file with sudo. Don't really know how to begin.

How do I edit a file using sudo?

Thanks.

---

### Post by kevdog on 2007-06-05
If your are using ubuntu, type
sudo gedit /etc/modprobe.d/ndiswrapper 
on the command line. 

Make the changes, and save the file.
Thats it.

---

### Post by scottDkoDer on 2007-06-05
Alright.  I usually spend more time doing and less time reading and posting, so here my contrib.  Its been at least 3 days since I've downloaded Feisty and have been trying to install ndiswrapper, but wierd stuff... the packaged ndiswrapper didn't work.  So I downloaded different debs and got it to work with v1.9 on the live cd, but rebooted and the identical commands didn't work.  *intermittent problems ARE the worst* Anyway, everybody said compile from source it works, and i said how to install build-essential without the internet?? I'm posting from livecd now and will reinstall feisty and try then (I think I got it this time)

```
ubuntu@ubuntu:~$ sudo apt-cdrom add
Please insert a Disc in the drive and press enter
ubuntu@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
ubuntu@ubuntu:/media/disk/home/scott/Desktop$ cd ndiswrapper-1.46
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ ls
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo make
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo make install
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-15-generic SMP mod_unload 586 
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ ndiswrapper -l
ls: /etc/ndiswrapper: No such file or directory
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo ndiswrapper -i /media/disk-1/Linux-bak/Belkin/net5416.inf
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ ndiswrapper -l
net5416 : driver installed
        device (168C:0023) present
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo modprobe ndiswrapper
ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ sudo iwconfig wlan0 essid MOKITUMNETT key ********** && sudo dhclient3 wlan0 && iwconfig
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:50:f6:c4:be
Sending on   LPF/wlan0/00:11:50:f6:c4:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.109 -- renewal in 42548 seconds.
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"MOKITUMNETT"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:06:57:E0   
          Bit Rate=11 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:/media/disk/home/scott/Desktop/ndiswrapper-1.46$ 


```

I edited some of the output code to reduce size, so yours may look different.  This assumes you already downloaded and untared the source code for ndiswrapper.  I used v 1.9_1.46 but I think just by doing the make uninstalls, compiling, and reinstalling does the trick.  The madwifi-ng drivers work too after compiling.  Hope this helps! ;)

---

### Post by scottDkoDer on 2007-06-05
OK. Now I have Feisty installed and successfully compiled and installed ndiswrapper.  A couple of snags were I had to # out all the sources.list entries except the cdrom and had to do an apt-get udate. Otherwise it would try to d/l from the net. (doesn't work when your trying to install network drivers).  And not being able to use the 'cd' command without loging in as root ;- not just sudo, but sudo su.  Just to change dirs?? I hope this isn't another bug...

---

### Post by Chet Hardin on 2007-06-05
So I tried to reinstall ndiswrapper (I am getting frustrated). When I ran make install at the root, this is what I got, a long string of errors. Ideas?:


root@chet-laptop:/home/chet/ndiswrapper-1.46# make install
make -C driver install
make[1]: Entering directory `/home/chet/ndiswrapper-1.46/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/chet/ndiswrapper-1.46/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/chet/ndiswrapper-1.46/driver/built-in.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/crt.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/hal.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/iw_ndis.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/loader.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/ndis.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/ntoskernel.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/ntoskernel_io.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/pe_linker.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/pnp.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/proc.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/rtl.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/wrapmem.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/wrapndis.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/wrapper.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/usb.o
  CC [M]  /home/chet/ndiswrapper-1.46/driver/divdi3.o
  LD [M]  /home/chet/ndiswrapper-1.46/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chet/ndiswrapper-1.46/driver/ndiswrapper.mod.o
  LD [M]  /home/chet/ndiswrapper-1.46/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
make[1]: Leaving directory `/home/chet/ndiswrapper-1.46/driver'
make -C utils install
make[1]: Entering directory `/home/chet/ndiswrapper-1.46/utils'
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
make[1]: Leaving directory `/home/chet/ndiswrapper-1.46/utils'
make: *** [install] Error 2

---

### Post by kevdog on 2007-06-05
Although you will likely deviate from this guide: [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689), it does a great job explaining the installation of ndiswrapper and things you need to get in installed.  I dont know if you are using a broadcom based chipset card, so I would follow it up to the point until you actually install the broadcom driver

ndiswrapper -i (filename).

Hopefully this will help.

---

### Post by scottDkoDer on 2007-06-05
Chet:

Make sure you have build-essential installed and the correct headers for your kernel.

---

### Post by Chet Hardin on 2007-06-05
Hey Scott. How do I check my kernel headers? And what is build-essential? Thanks!!!

---

