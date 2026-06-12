---
title: "DWL-G132 = no wlan0?"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by SanguineIllusion on 2006-10-27
Okay guys, I finally got Ubuntu fixed and booted and I seem to have encountered a whole new problem that I have wasted my entire friday afternoon/evening on. YAY! :( 

Okay so I downloaded the newest windows drivers for this dwl-g132 usb wireless adapter and used ndiswrapper -i to install both athfmwdl.inf and neta5agu.inf. ndiswrapper -l shows both drivers are installed and the hardware is present.

Sounds good but the only items in administration>networking are the two wired connections that I don't use (eth0 and eth1). Ive been trying stuff that people in IRC are suggesting all night but its like wlan0 does not exist. For example, i tried ifup wlan0 and it just says that it doesn't exist. I can clearly see the thing in device manager :( 

I am at my wits end here, and the two IRC channels I've been trying to get help on won't even talk to me anymore. I've followed all the guides that have been thrown at me and still nothing. 

Oh and if this is relevant, for some reason ndiswrapper -m results in "modprobe config already contains alias directive". I'd appreciate any and all help you guys have to offer, I'm out of people to turn to.

---

### Post by justintime32 on 2006-10-28
Why would you install two drivers for one device?

---

### Post by SanguineIllusion on 2006-10-28
Because there are 2 drivers in the driver directory for this adapter and I believe they aren't opposing drivers. 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D) shows that the DWL-G132 Rev A2 uses both drivers:

"Other: With ndiswrapper version 1.7 (and later), load_fw_ar5523 is not used; instead, install both neta5agu and athfmwdl drivers. With that, ndiswrapper will load the firmware when necessary."

I started with just neta5agu and it still wasn't working. This is really confusing because its showing both drivers as working and hardware present but it always says no such device in reference to wlan0.

Any ideas? I'm willing to try anything here.

---

### Post by justintime32 on 2006-10-28
Have you tried it without ndiswrapper? It's an Atheros card, which should work natively with Linux.

---

### Post by justintime32 on 2006-10-28
Also, please run the 'dmesg' command in a terminal and post the output.

---

### Post by SanguineIllusion on 2006-10-28
> **justintime32 said:**
> Have you tried it without ndiswrapper? It's an Atheros card, which should work natively with Linux.

I'm very new to Ubuntu and have forgotten most of the stuff I learned about linux. I just saw that the device wasn't in administration>networking and so I sought out help. I'd be more than welling to not use ndiswrapper, but remember that I'm a total noob and so I need some directions before I can do something like that.

> **justintime32 said:**
> Also, please run the 'dmesg' command in a terminal and post the output.

Can you give me a specific part to look for? The output is MASSIVE and since I can't get on the internet on the computer with Ubuntu, I can't really copy and paste it.

---

### Post by justintime32 on 2006-10-28
Try "dmesg | grep ndis". That should narrow it down.

---

### Post by SanguineIllusion on 2006-10-28
> **justintime32 said:**
> Try "dmesg | grep ndis". That should narrow it down.

Ah that did the trick. 2 lines:
[17179598.868000] ndiswrapper version 1.27 loaded (preempt=no, smp=yes)
[17179598.884000] usbcore: registered new driver ndiswrapper

---

### Post by SanguineIllusion on 2006-10-28
Ok, an update for you all. I was trying to find out what version of ndiswrapper I had installed and stumbled upon a problem. ndiswrapper -v wasn't showing the version of ndiswrapper, but returned an error. I went back into the ndiswrapper 1.27 directory that I had extracted and ran make install again and lo and behold, ndiswrapper -v now shows a version like it's supposed to.

I uninstalled both drivers, reinstalled them and this time when I type ndiswrapper -l, its more specific. It now shows the device ID with the "hardware present" part:

neta5agu     driver installed
athfmwdl     driver isntalled, hardware (2001:3A03) present

The troubling part though is that neta5agu no longer shows hardware present. I'm not sure its supposed to though considering that athfmwdl is showing the hardware present. I don't know how relevant this is but I feel myself getting closer to a solution. iwconfig still doesn't show wlan0 or anything close to it.

Please let me know if you guys have any idea on how to fix this :neutral:

---

### Post by SanguineIllusion on 2006-10-29
Ok guys, final update, I seemed to have fixed it. I was kind of curious why ndiswrapper -r was producing an error so I did a make install again of ndiswrapper. At first it didn't work and I was completely distraught, but someone simply suggested that I do modprobe -r ndiswrapper; modprobe ndiswrapper and sure enough it worked! I've never been so happy to see the internet in my life :p

---

### Post by Sfacs on 2006-10-29
Hi!

I've also got the DWL-G132, and I would like to know how do you exactly install ndiswrapper?


I downloaded the tar.gz but when I try to extract it, I've got many errors..

---

### Post by SanguineIllusion on 2006-10-29
I extracted the tar.gz, CDed to the directory and then I believe I did:

make distclean
make
make install

If you end up with any errors you might want to check here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Errors_on_Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Errors_on_Installation)

---

### Post by Sfacs on 2006-10-29
When I launch the make command, I've got these errors..

```
/ndiswrapper-1.28# make
loadndisdriver.c:15:20: error: stdlib.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:16:19: error: stdio.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:17:19: error: errno.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:18:20: error: string.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:19:20: error: libgen.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:21:22: error: sys/mman.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:23:23: error: sys/types.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:24:23: error: sys/ioctl.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:25:22: error: sys/stat.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:26:20: error: unistd.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:27:19: error: fcntl.h: Aucun fichier ou répertoire de ce type
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:29:19: error: ctype.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:30:20: error: dirent.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:31:20: error: syslog.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:34:25: error: linux/major.h: Aucun fichier ou répertoire de ce type
loadndisdriver.c:35:25: error: linux/ioctl.h: Aucun fichier ou répertoire de ce type
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
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:219: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:219: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:221: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:223: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:224: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:226: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:232: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:234: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:234: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:234: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:252: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:254: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:262: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:264: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:270: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:270: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:274: warning: implicit declaration of function ‘memset’
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:275: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:283: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:283: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:285: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function ‘stat’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:320: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:321: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:285: warning: unused variable ‘statbuf’
loadndisdriver.c:347: error: expected expression before ‘struct’
loadndisdriver.c:349: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:351: warning: implicit declaration of function ‘free’
loadndisdriver.c:358: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:371: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:374: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:377: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:378: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:380: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:380: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:403: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:371: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:415: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:415: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:420: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:422: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:425: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:430: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:431: error: dereferencing pointer to incomplete type
loadndisdriver.c:432: error: dereferencing pointer to incomplete type
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:444: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:461: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:461: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:469: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:469: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:470: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:470: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:485: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:486: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:486: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:486: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:488: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:493: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:509: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:509: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:513: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:515: warning: implicit declaration of function ‘printf’
loadndisdriver.c:515: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:525: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:540: warning: implicit declaration of function ‘atof’
loadndisdriver.c:547: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:554: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:588: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Erreur 1
make: *** [all] Erreur 2
root@sfacs-desktop:/media/Partage/ndiswrapper-1.28# 

```


What did i forget? :(

---

### Post by SanguineIllusion on 2006-10-29
Unforunately, I'm way too inexperienced with Ubuntu to be able to figure that out (especially since a lot of it looks like its in a foreign language). I would post that in its own thread and see if you can get someone to help you out. Good luck!

---

### Post by AgeMO on 2007-07-27
you need to install build essential

---

