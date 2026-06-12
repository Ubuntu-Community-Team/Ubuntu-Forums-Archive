---
title: "Wifi on new Thinkpad T60?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by bjorntj on 2007-04-23
I have just installed Ubuntu 7.04 on my new T60 and it seemt to work fine, except for my wifi card...
lspci -v give me this..:

```

03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
        Subsystem: Atheros Communications, Inc. Unknown device 0033
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at edf00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

Any way to get this "card" working?


Regards,

BTJ

---

### Post by chili555 on 2007-04-23
There are two Atheros cards used in versions of the T60: AR5006EX and AR5008. You can read here: [http://www.thinkwiki.org/wiki/Category:T60](http://www.thinkwiki.org/wiki/Category:T60) the fix for both is the same, either madwifi or ndiswrapper. There are links to madwifi.

Post back if you need more help.

---

### Post by bjorntj on 2007-04-23
Oki... I think I have the n version of the card.... And I have installed the windows driver with ndiswrapper and iwconfig shows my wifi card... also the networkmanager applet show all the available wireless networks but I am not able to connect to any networks... I get asked for WPA key, which I should, but I get no connect...


BTJ

---

### Post by bjorntj on 2007-04-23
I also tried compiling svn version of madwifi but I can't compile it, I only get..:

```

make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath/if_ath.o
  CC [M]  /home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath/if_ath_pci.o
  LD [M]  /home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath/ath_pci.o
  CC [M]  /home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/ah_os.o
  HOSTCC  /home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: At top level:
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c: In function 'main':
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal/uudecode] Error 1
make[2]: *** [/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10/ath_hal] Error 2
make[1]: *** [_module_/home/bjorntj/ftp/m/madwifi-hal-0.9.30.10] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

```


What am I missing?


BTJ

---

### Post by bjorntj on 2007-04-23
Some header files it look like.... Which packages do I need to install?

BTJ

---

### Post by chili555 on 2007-04-23
Please be sure you have linux-headers-`uname -r` and build-essential installed, which you can get through Synaptic or apt-get.

I followed this how-to: [http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008) and 'make' ran without any errors or warnings. To use svn, you will also need to install subversion.

---

### Post by bjorntj on 2007-04-23
I was missing build-essential, after I installed this I could compile the madwifi module and it loaded ok also...
Now I have to wait until I get home to check how it works... Thx.... :)

BTJ

---

### Post by thushw on 2008-05-05
did you get this to work?
thx,

---

### Post by bjorntj on 2008-05-05
Well, yes... But madwifi still has a bug that makes the wifi network lock after x hours of use and the "only" way to make it work again, is to reboot...


BTJ

---

### Post by klaasvanschelven on 2008-05-05
I have a laptop here too that says "Lenovo Thinkpad T60" on it... but has a Atheros AR5418 instead. I've done the above (madwifi build and then modprobe).(8.04 Heron) 

```
$ lshw -C network
  *-network               
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
  *-network
       description: Wireless interface
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:91:17:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11a
```

So far so good (without building it it was unclaimed).
However: the icon in the corner does not allow me to select a wireless network as it does on my own laptop - going from roaming mode to fixing the access point in the Admin network. wifi-radar shows me the network... but I can't figure out how to connect and where to put my wep key.

I seem so close... any ideas on what this can be? Thanks

---

### Post by chili555 on 2008-05-05
Network Manager, which is installed by default, will not let you connect wirelessly if you have a working IP address wired, which you do:```
ip=192.168.2.102 latency=0 link=yes
```Please detach the wire and restart networking:```
sudo /etc/init.d/networking restart
```and see if your wireless comes to life.

---

### Post by klaasvanschelven on 2008-05-06
It works... it works :-)

Prev. post did the trick in the end (taking out wire, restarting)...

---

