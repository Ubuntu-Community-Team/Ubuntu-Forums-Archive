---
title: "Atheros AR5418 not recognized"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by mlilien on 2007-10-23
I posted on a thread in the hardware and laptops forum earlier today ([http://ubuntuforums.org/showthread.php?t=578778](http://ubuntuforums.org/showthread.php?t=578778)) with a bunch of people that had my same problem, but I thought we might get more help here.

I have Lenovo t60p that I just upgraded to Gutsy.  I did a fresh install from Feisty, where I had used madwifi to get the wireless card working.

However, I can't seem to replicate that in Gutsy.

In fiesty, I followed the directions here [http://forum.thinkpads.com/viewtopic.php?t=43159&highlight=](http://forum.thinkpads.com/viewtopic.php?t=43159&highlight=), but the link to get the madwifi source there doesn't work.  I downloaded the latest release from madwifi.org, but was unable to compile it (what repositories do I need?).

The Lenovo site says I should have an ipw3945 card,which should be supported in gutsy, but I don't see an option for it in the restricted drivers.

The output of lshw -C network is:

```

description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:1a:6b:67:85:ca
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.2.102 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
*-network UNCLAIMED
description: Network controller
product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list
configuration: latency=0

```

Thank you in advance for any help.

---

### Post by Lambert on 2007-10-24
1. no it's not an ipw3945 wireless device according to lshw
2. doing some searching shows users just installing the linux-restricted package-xxxx (which includes the madwifi driver) gets this device working.

Did you install linux-restricted package from the repository? If not try that first.

---

### Post by mlilien on 2007-10-24
Yeah.  I have that installed already.  What about following the directions that worked in feisty?

> 

mkdir madwifi
cd madwifi
wget [http://snapshots.madwifi.org/madwifi-hal-0.9.30.13/madwifi-hal-0.9.30.13-r2351-20070519.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.13/madwifi-hal-0.9.30.13-r2351-20070519.tar.gz)
mv madwifi-hal-0.9.30.13-r2351-20070519 madwifi
wget [http://people.freebsd.org/~sam/ath_hal-20070428.tgz](http://people.freebsd.org/~sam/ath_hal-20070428.tgz)
tar xvzf ath_hal-20070428.tgz
rm -rf ./madwifi/hal/
cp ath_hal-20070428 madwifi/hal -R
cd madwifi
make clean
make
sudo make install


It will give you the option to remove all existing drivers. I did so.

sudo rmmod `lsmod | egrep 'ath|wlan' | sed 's@ .*@@'`
sudo modprobe ath_pci 


I can't find that madwifi release, but I would assume using the current one should work.  But I tried it and got nothing.  Do I need to do something else?

What about buying and then installing a new wireless card?  Would it be recognized immediately or would I have to do something else to get it working?

---

### Post by rustybronco on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY](http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY)

---

### Post by mlilien on 2007-10-24
Thanks.  That worked perfectly.

---

### Post by charles_316 on 2007-11-15
After trying that Thinkwiki tutorial, I get the following error are puttin in "make"

charles@charles-laptop:~/madwifi/trunk$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/charles/madwifi/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/charles/madwifi/trunk/ath/if_ath.o
  CC [M]  /home/charles/madwifi/trunk/ath/if_ath_pci.o
  LD [M]  /home/charles/madwifi/trunk/ath/ath_pci.o
  CC [M]  /home/charles/madwifi/trunk/ath_hal/ah_os.o
  HOSTCC  /home/charles/madwifi/trunk/ath_hal/uudecode
/home/charles/madwifi/trunk/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/charles/madwifi/trunk/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/charles/madwifi/trunk/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c: At top level:
/home/charles/madwifi/trunk/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/charles/madwifi/trunk/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/charles/madwifi/trunk/ath_hal/uudecode.c: In function 'main':
/home/charles/madwifi/trunk/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/charles/madwifi/trunk/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/charles/madwifi/trunk/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/charles/madwifi/trunk/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/charles/madwifi/trunk/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/charles/madwifi/trunk/ath_hal/uudecode] Error 1
make[2]: *** [/home/charles/madwifi/trunk/ath_hal] Error 2
make[1]: *** [_module_/home/charles/madwifi/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

---

### Post by tabithaboof on 2007-11-17
I got exactly the same error when trying to compile, unfortunately no idea what it means. Anyone have any ideas?

---

### Post by charles_316 on 2007-11-18
bump 

i think the #include doesn't link to the correct directories... where are the header files like stdio.h located?

---

### Post by charles_316 on 2007-11-30
bump

---

### Post by langer3 on 2007-12-08
I had the same problem and was able to fix the error by installing the following:

```


sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r`


```

---

### Post by charles_316 on 2007-12-17
for some reason when i use the command LSHW -C network, i can see that my wireless is disabled:

  *-network DISABLED
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:b2:3f:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci mul

How do i enable it?

---

