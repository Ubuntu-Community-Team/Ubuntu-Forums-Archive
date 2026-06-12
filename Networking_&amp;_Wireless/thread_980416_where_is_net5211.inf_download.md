---
title: "where is net5211.inf download"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by steve228 on 2008-11-12
where can i find and download the net5211.inf file so I can use the ndisgtk command? 

Thanks

---

### Post by cariboo on 2008-11-12
You can get it here:

[http://www.netgate.com/support/Drivers/](http://www.netgate.com/support/Drivers/)

I'm not really sure you need it though as there is an Atheros driver built into the kernel.

Could paste the output of:

```
sudo lshw -C network
```

in your next post. The above command must be typed in a Applications-->Accessories-->Terminal.

Jim

---

### Post by steve228 on 2008-11-13
thank you and here is the output from that command...

```
steve@steve-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:a4:7b:77
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:5e:94:12:d2:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


Also: whenever i used ndisgtk, it successfully installed the driver, but said my hardware was not present.  I know that my adapter works, because I am dual booting with Windows.  Any suggestions?

---

### Post by enigmageek on 2008-11-13
Hello. Go here [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
and download the madwifi-hal. I'm using the 3835 one. Go to System/Administration/Hardware Drivers Manager and uncheck atheros support and hal support. Also make sure you have build-essentials package installed.
Uncompress the madwifi-hal into a folder. Mine is in /home/myname. In the Terminal type:
   
cd /home/username/madwifi-hal-0.10.5.6-r3835-20080801....then
sudo make install...then cd
gksu gedit /etc/modprobe.d/blacklist
at the end of the file add
blacklist ath5k
save file and exit
reboot

Good luck I hope this helps.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5

---

### Post by steve228 on 2008-11-15
ok I tried using madwifi and here is what happened:

```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: At top level:
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c: In function 'main':
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal/uudecode] Error 1
make[2]: *** [/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604/ath_hal] Error 2
make[1]: *** [_module_/home/steve/Desktop/madwifi-hal-0.10.5.6-r3698-20080604] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2


```


Also, I have absolutely NO connection to the internet through ubuntu so I cannot use 'sudo apt-get' to get build-essential or any other packages.  I have to manually download each package.  There is no support for neither my wireless nor my ethernet wired connection.

---

### Post by enigmageek on 2008-11-19
Hello Steve228. Sorry madwifi doesn't work for you. It's strange that not even a wired connection works. I wonder if Network Manager is damaged. I can package the 5211 drivers, includes the sys, net, and inf files to use with ndisgtk and send. Good luck!

---

