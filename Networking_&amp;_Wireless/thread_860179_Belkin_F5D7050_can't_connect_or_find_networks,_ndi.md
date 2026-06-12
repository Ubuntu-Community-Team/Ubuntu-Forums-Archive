---
title: "Belkin F5D7050 can't connect or find networks, ndiswrapper not working, Hardy"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by gavygavgav on 2008-07-15
After some research, it seemed that the Belkin W5D7050 was the best bet to connect my Hardy desktop to wireless networks.  Alas, the claims of it being ready out of the box did no good for me.

I right click on the Network Manager icon (two computers with a red and white X) and find "Enable Networking" checked, "Connection Information" greyed out, and click on "**Edit Wireless Networks**".  It immediately opens to **show NO networks**.  The lights on my USB adapter are off from boot to shutdown, and it works in my XP other boot.

I've tried many different approaches found here and elsewhere to get it working, none of which worked.  Most were halted by my inability to do anything so simple as install a program, some by the fact that I CAN'T download a package without internet in Linux!  The best guide I found was [here]("http://opensource.bureau-cornavin.com/belkin/index.html"), and got so far as having to install my zd1211 driver, but when I downloaded and unzipped it, there was no Makefile to edit as the walkthrough commands!!

Specs: Ubuntu Hardy Heron 8.04, Belkin Wireless G USB Adapter "Ver.5000" F5D7050

Here's the results of some common commands I see others recommending:
```
$ lsusb
Bus 005 Device 003: ID050d:705e Belkin Components
```

```
$ iwconfig
lo     no wireless extensions.

eth0   no wireless extensions.
```

```
$ modprobe zd1211b
FATAL: Module zd1211b not found
```

```
$ modprobe zd1211rw
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211 (/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
```

I even tried ndiswrapper, which somehow didn't install on my system.  That may be just as well, as I'd prefer to keep the solution simple.


:confused::confused::confused:PLEASE HELP!!!!:confused::confused::confused:

---

### Post by gavygavgav on 2008-07-15
And now I tried installing **ndiswrapper 1.53** following the instructions in the package.  This resulted in many messages such as "**error: 'DIR' undeclared**" followed by messages such as "**warning: implicit declaration of function 'memset'**"

My research implies that I need **build-essential**.  However, when I tried installing that, it told me I need some 8 other packages which I can't get because I can't get online!!!!  So any solution **without ndiswrapper** is best!  Or just tell me how to install it without build-essential.

---

### Post by jingo811 on 2008-07-15
I wanted to wait until some of the Network veterans in here would give you some official solutions.  But since you've been forced down the NDISwrapper path in the end, with no wired NIC to make your wireless device work try these steps.

[http://virtualseafarer.com/witch/ndiswrapper/index.html#](http://virtualseafarer.com/witch/ndiswrapper/index.html#)

---

### Post by gavygavgav on 2008-07-15
Thank you for the link, Jingo.  I followed the instructions up to page 4, step 3.  The "**make uninstall**" command went well, but this is (and has been) my results with the "**sudo make**" command:

```
gavin@gavin-desktop:~/ndiswrapper-1.53$ sudo make
make -C driver
make[1]: Entering directory `/home/gavin/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/gavin/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/home/gavin/ndiswrapper-1.53/driver'
make -C utils
make[1]: Entering directory `/home/gavin/ndiswrapper-1.53/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:28: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/gavin/ndiswrapper-1.53/utils'
make: *** [all] Error 2
gavin@gavin-desktop:~/ndiswrapper-1.53$
```

"**sudo makeinstall**" has the same sort of results.  So at this point, the problem is installing ndiswrapper.

EDIT: is it possible I unzipped this into the wrong directory?  I just unzipped it into my "Home" folder, so should I try again with a different one?  I'm just throwing out ideas here.

---

### Post by gavygavgav on 2008-07-15
**UPDATE:** I just loaded ndiswrapper successfully, I think.  I had to install linux-libc-dev and libc6-dev.  It seemed to accept the driver from the CD for the USB device.  However, on reboot still no lights on the adapter and iwconfig and ifconfig both report only "lo" and "eth0".

$ ndiswrapper -l reports
```
blkwgu: driver installed
      device (050D:705E) present
```

This is the same ID as reported by lsusb.

I did $ modprobe ndiswrapper, both as user and su, but the result remained ```
lo     no wireless extensions.
eth0     no wireless extensions.
```

---

### Post by gavygavgav on 2008-07-15
IT WORKS!!  I'm not sure why, but a restart did the trick.  To summarize my actions for anyone up the same creek, I had to properly install NDIS, which required various libraries, and then NDIS required a 32-bit driver and a restart.  I'll inform if there are any further complications, thank you very much, jingo!!!

---

### Post by Gibbs on 2008-07-15
I installed something similar yesterday. When it's not working I find running a scan from the terminal (**sudo iwlist wlan0 scan**) or forcing wlan0 up (**sudo ifconfig wlan0 up**) does the trick.

---

### Post by jingo811 on 2008-07-15
> I had to install linux-libc-dev and libc6-dev.
That's weird that Hardy 8.04 needed you to install those packages.  In the older versions of Ubuntu like my Feisty 7.04 it's already pre-installed.

Good to hear that you solved things b'coz I have no idea what went wrong judging from your previous reports :)

If my tutorial worked for you then you might be interested in my automated bash script that basically does the same thing but in ~30 seconds.
In case you need to do the entire process again.
[http://ubuntuforums.org/showthread.php?t=860090](http://ubuntuforums.org/showthread.php?t=860090)

All you have to do is place the Wireless Windows drivers and NDISwrapper tar file in the TOURIST folder.  Then execute the script.

---

