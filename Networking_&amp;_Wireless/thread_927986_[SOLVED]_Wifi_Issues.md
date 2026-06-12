---
title: "[SOLVED] Wifi Issues"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2008-09-23
Hello, I am completely new to Linux, I'm quite advanced in Windows and been their all my life, so I thought I try Linux, at first I went with Kubuntu but couldn't get my wifi working and so after following verious threads and trying to get it working but failing, I decided to install Ubuntu 8.04.1. And I still have the same problems.

I have a Toshiba Satellite A205-S5825
Hardware Drivers says I have proprietary drivers installed;
Atheros Hardware Access Layer (HAL)
Support for Atheros 802.11 wireless LAN cards
Both Enabled and status says "In use"
I've tried searching for the driver but Toshiba would not tell me, I found another thread of someone explaining that a driver (XP) for a different Toshiba Laptop worked, so I've downloaded that. 
Network Settings does not show a Wireless connection only a Wired, P2P.

I am a complete newbie to so please keep things simple.
Thank you.

---

### Post by qstraza on 2008-09-23
well first of all, whats your output on ```
sudo iwconfig
```

and also paste the ouput of```

lspci
```

---

### Post by AmbiguousOutlier on 2008-09-23
> **qstraza said:**
> 
```
sudo iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.


> **qstraza said:**
> 
```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by qstraza on 2008-09-23
Well first of all check that you have turned bluetooth/wifi on. On your laptop (hardwarish) i mean.

You could try installing madwifi, but i think this should be automaticly installed.

whats your output of "dmesg" ?

---

### Post by qstraza on 2008-09-23
try this:
[http://ubuntuforums.org/showpost.php?p=5120351&postcount=12](http://ubuntuforums.org/showpost.php?p=5120351&postcount=12)

---

### Post by AmbiguousOutlier on 2008-09-23
dmesg wouldn't return everything and ran out of space. I did install madwifi yesterday on Kubuntu but it didn't work, it came up with an error which I can't remember now. I think it was essential build not installed or something.

---

Too big to paste so I have attached it.

EDIT:

just retrying madwifi

---

### Post by AmbiguousOutlier on 2008-09-23
I know I need to extract the file but I don't know where it has put it, or even how to unless all it involves is double clicking a file.

madwifi output:

rhys@Orange:~$ wget [http://sourceforge.net/project/downloading.php?groupname=madwifi&filename=madwifi-0.9.4.tar.gz&use_mirror=surfnet](http://sourceforge.net/project/downloading.php?groupname=madwifi&filename=madwifi-0.9.4.tar.gz&use_mirror=surfnet)
[1] 6174
[2] 6175
[2]+  Done                    filename=madwifi-0.9.4.tar.gz
rhys@Orange:~$ --21:06:03--  [http://sourceforge.net/project/downloading.php?groupname=madwifi](http://sourceforge.net/project/downloading.php?groupname=madwifi)
           => `downloading.php?groupname=madwifi.2'
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                ] 28,244        90.90K/s             

21:06:04 (90.62 KB/s) - `downloading.php?groupname=madwifi.2' saved [28244]


[1]+  Done                    wget [http://sourceforge.net/project/downloading.php?groupname=madwifi](http://sourceforge.net/project/downloading.php?groupname=madwifi)
rhys@Orange:~$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by qstraza on 2008-09-23
```
mv "downloading.php?groupname=madwifi.2" madwifi.tar.gz
tar zfxv madwifi.tar.gz
cd madwifi*
make

```
something like that

---

### Post by AmbiguousOutlier on 2008-09-23
Just so you are aware none of this makes any sense to me. On a side note is there a "*** for dummies" that I could read?

rhys@Orange:~$ mv "downloading.php?groupname=madwifi.2" madwifi.tar.gz
rhys@Orange:~$ tar zfxv madwifi.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by qstraza on 2008-09-23
```
wget http://heanet.dl.sourceforge.net/sourceforge/madwifi/madwifi-0.9.4.tar.gz
tar zfxv madwifi-0.9.4.tar.gz
cd madwifi*
make

```

does this work? :p

---

### Post by AmbiguousOutlier on 2008-09-23
I got this;

rhys@Orange:~/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/rhys/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/rhys/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/rhys/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/rhys/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/rhys/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/rhys/madwifi-0.9.4/ath_hal/uudecode
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/rhys/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/rhys/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/rhys/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/rhys/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

---

### Post by qstraza on 2008-09-23
try searching for deb package of madwifi, this way you will avoid compiling...

---

### Post by AmbiguousOutlier on 2008-09-23
Sorry I'm lost.

---

### Post by qstraza on 2008-09-23
[http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)

im googling instead of you...

---

### Post by AmbiguousOutlier on 2008-09-23
Sorry, 

I tried something along those lines earlier, when I tried it now i got this;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

