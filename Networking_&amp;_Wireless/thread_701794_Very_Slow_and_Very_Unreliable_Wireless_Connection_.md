---
title: "Very Slow and Very Unreliable Wireless Connection on RTL8187"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Bridger987 on 2008-02-19
**[COLOR=Red]EDIT:  Solved by upgrading to Ubuntu Hardy 8.04 LTS.[/COLOR]**

First off, I realize that the following thread exists:
[http://ubuntuforums.org/showthread.php?t=634949](http://ubuntuforums.org/showthread.php?t=634949)

But, that thread does not detail any sort of solution to the problem.  I just installed Ubuntu onto my laptop, and have been -very- happy with the results.  The only problem is, my wireless card's signal is constantly unreliable.  The signals that it does pick up on are weak and seem to drop almost immediately, even though they worked perfectly when I was running Windows XP Media Center Edition last week.

If anyone has a solution for this, I'd appreciate it.

Thanks! :KS

---

### Post by jhetrick62 on 2008-02-19
Build a new wireless driver using the original windows drivers with ndiswrapper, blacklist your linux driver and it should work just fine.

Ralink chips seem very un-reliable on the Linux driver from my experience.  I used ndiswrapper this weekend to solve a problem like this.

network manager still leave a lot to be desired, but it worked after I re-built.

Jeff

---

### Post by afterwego on 2008-02-19
The RTL8187 is actually a Realtek chip not Ralink. I too have that chip in my laptop. Anyway after using NDISWrapper and the Windows drivers I have been having consistently dropped connections that last from either a few seconds to a couple of minutes, so I don't know how much luck you will have with yours. I have a WPA protected network and there are no existing drivers to blacklist.

Things I have tried consist of:
[LIST]
[*]Compiling NDISWrapper from source
[*]Tried Windows 98, Windows XP, and Windows Vista drivers
[*]Disabled TCP/IP v6
[*]Watched /var/log/syslog, dmesg, and iwevent for anything noticeable. (Can post if it will help)
[*]Disable roaming mode and manually set wireless details
[*]Set static IP for connection
[*]Install Wicd instead of Network Manager
[/LIST]

I have noticed several threads saying that this chipset worked fine using NDISWrapper under 7.04, but something changed in 7.10 that seems to have broke it. Sorry, I don't have an answer, but I am hoping that I can be of help to finding a solution as I have the same chip and would like mine to work as well :)

---

### Post by jhetrick62 on 2008-02-19
I don't use WPA but from memory I think that WPA is controlled by wpa_supplicant or a plugin like that.  Search the forum to see if that helps.

Jeff

---

### Post by sfleite on 2008-02-20
Hi.
For my conection problem I read this [http://ubuntuforums.org/showthread.php?p=4371034]("http://ubuntuforums.org/showthread.php?p=4371034") and a follow this instructions [http://aircrack-ng.org/doku.php?id=r8187]("http://aircrack-ng.org/doku.php?id=r8187") and my conection still run. But only if a encryption is WEP. I do not make a conection if a encryption os WPA/WPA2.
Any help?
And how I can remove this driver? I wish to try ndiswrapper and win98 drivers from this docuemntation
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek")
I'm a newbie on Linux.

Thanks.

Saulo Leite.

---

### Post by Bridger987 on 2008-02-24
Bumping my own thread.  ^_^  

Has anyone had this problem (see first post), and/or found instructions on how to fix it?  Again, my card is an inbuilt RTL-8187 which is not working as reliably since I installed Ubuntu, in comparison with Windows XP.  I would hate to have to switch back to XP just because of this.  Everything else is working well, and this is its only flaw (so far).

Thanks!

---

### Post by Bridger987 on 2008-02-24
> **jhetrick62 said:**
> Build a new wireless driver using the original windows drivers with ndiswrapper, blacklist your linux driver and it should work just fine.

Ralink chips seem very un-reliable on the Linux driver from my experience.  I used ndiswrapper this weekend to solve a problem like this.

network manager still leave a lot to be desired, but it worked after I re-built.

Jeff

Jeff,

I do have Windows drivers at hand (I recently downloaded them), and I have the Ubuntu ndiswrapper GUI working.  But how would I go about blacklisiting my linux driver?

Thanks!

---

### Post by jhetrick62 on 2008-02-24
Bridger,

If you don't blacklist it properly, odds are it will reload the original drivers.  Also, you downloaded the windows drivers, did you download the WinXP drivers?  Vista does not work many times.

To find out what driver is being used, use the command: 
 lshw -C network

This will give you listing like this: (I took this off of Kevdog's howto as I'm not on a wireless computer right now)

*-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **bcm43xx** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

As you can see, this one is using the bcm43xx driver and that would be the blacklisted driver in this case.  If you find that ndiswrapper is not being used with your wireless interface, then modify the blacklist file by adding to the bottom of the blacklist file using this command to open it with gedit.
sudo gedit /etc/modprobe.d/blacklist

Then add "blacklist your_driver_name" to the bottom of the file.  Save the file and reboot your computer and your original driver will now be blacklisted if it is still being used.

Here is the link for Kevdog's howto as it's very in depth and may answer any other questions.  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Goodluck,
Jeff

---

### Post by Bridger987 on 2008-02-24
Jeff,

The output for my wireless card does not seem to mention a driver.  Here's what came up:

```
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:cf:ec:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11g

```

---

### Post by jhetrick62 on 2008-02-24
Ok,

Did you review Kevdog's howto on installing Ndiswrapper?  It appears that possibly Ndiswrapper isn't working properly.  It should have come up as the driver if no other driver was present and you have it installed properly.

What do you get with Ndiswrapper -l command?  Does it list your driver that you built?
What about modprobe -l command | grep ndiswrapper ?  Does it list ndiswrapper as an installed module?

Jeff

---

### Post by Bridger987 on 2008-02-24
Wait a moment... was I supposed to set up the windows driver using ndiswrapper -before- I brought that up?

*Grins*  This shows you how much of a newbie I am at this. :lolflag:

---

### Post by jhetrick62 on 2008-02-24
Well, at least your old driver did not appear to be loading.  Now setup ndiswrapper following Kevdog's guide and hopefully all will be well.

Goodluck,
Jeff

---

### Post by Bridger987 on 2008-02-28
Hmm... Ndiswrapper already appeared to be set up.  I installed the Windows driver using the Ubuntu application (System > Administration > Windows Wireless Drivers), and when I used the "lshw -C network" command, it still didn't list any driver being used.

I scoured the Realtek website, and amazingly enough, I found an OEM Linux driver for the RTL 8187L (my card is listed on the bottom of my laptop as only the "RTL8187"... so I am unsure about the model number).  If it is the correct model, however... how would I go about installing and setting up this driver to use with my wireless card?  Because if there is no driver being used... could that account for my horrible wireless performance?

Thanks :)

---

### Post by jhetrick62 on 2008-02-29
Just because Ndiswrapper is running doesn't mean that you built the windows driver.  Installing with Windows wireless drivers, may or may not work.  Do it the long way as it was described in Kevdog's howto.

That will work,
Jeff

---

### Post by Bridger987 on 2008-02-29
Okay, I downloaded and extracted the ndiswrapper files to a folder on my desktop...  and I followed the steps shown in Kevdog's guide...

```

bridger@bridger-laptop:~/Desktop/ndiswrapper-1.52$ make distclean
make -C driver clean
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C utils clean
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
rm -f *~
rm -fr ndiswrapper-1.52 ndiswrapper-1.52.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C utils distclean
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
rm -f .\#*

```

Okay, that seemed to work...

The next thing it says to do is type "make"...

```

bridger@bridger-laptop:~/Desktop/ndiswrapper-1.52$ make
make -C driver
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/bridger/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/bridger/Desktop/ndiswrapper-1.52/driver/built-in.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/iw_ndis.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/loader.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/ndis.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/ntoskernel.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/ntoskernel_io.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/pe_linker.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/pnp.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/proc.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/rtl.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/wrapmem.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/wrapndis.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/wrapper.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/usb.o
  CC [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/divdi3.o
  LD [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/bridger/Desktop/ndiswrapper-1.52/driver/ndiswrapper.mod.o
  LD [M]  /home/bridger/Desktop/ndiswrapper-1.52/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C utils
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
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
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
make: *** [all] Error 2

```

Hmm... that came out with a few errors.  I'll try the next step anyway, but if it doesn't work, I'll know why.

```
bridger@bridger-laptop:~/Desktop/ndiswrapper-1.52$ sudo make install
[sudo] password for bridger:
make -C driver install
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/bridger/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.22-14-generic/misc
/sbin/depmod -a 2.6.22-14-generic -b /
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/driver'
make -C utils install
make[1]: Entering directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
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
make[1]: Leaving directory `/home/bridger/Desktop/ndiswrapper-1.52/utils'
make: *** [install] Error 2

```

And more errors.  Hmm.  Can anyone make anything of this?

I'm following KevDog's guide to installing ndiswrapper (which is located [here]("http://ubuntuforums.org/showthread.php?t=574501")).

---

### Post by jhetrick62 on 2008-03-01
Okay,

You said that ndiswrapper was installed so you should have only needed to build the driver and install it.  What does synaptic say?  Is ndiswrapper installed from some other manner than building it from source which is what Kevdog did?

If so, you don't need to re-build it, just use it to make and install the driver.

Jeff

---

### Post by Bridger987 on 2008-03-01
Yes, I had already checked Synaptec, and both Ndiswrapper packages (ndiswrapper-common, and ndiswrapper-utils-1.9) plus the GUI (ndisgtk) were installed.

I finally came across a windows driver that is supposed to work under Ndiswrapper for my chipset, but I still am not sure of how to find out what driver the system was using so that I can blacklist it.

And also, what do you mean when you talk about "building" a driver?

Thanks :)

---

### Post by renzokuken on 2008-03-03
you need to blacklist rtl8187, rtl and r8187 to use ndiswrapper.....that how i had it working

```
blacklist rtl
blacklist r8187
blacklist rtl8187
```

incidentally, the new kernel 2.6.23 (now default for Hardy) is supposed to have a proper rtl8187 driver loaded that works properly with no need for ndiswrapper. I have found guides on Gentoo and Arch but so far have been unable to get it working properly in Ubuntu or Linux Mint (had most success with Mint but stopped working after a few reboots)

---

### Post by Bridger987 on 2008-03-04
Thanks a lot! :)  I was able to find a driver that sort of works... meaning that it can detect the network card, and find networks.  But in terms of connecting to them, it was working worse than the original linux drivers.

Does anyone know of anything else that can be done to get my card working reliably?

---

### Post by grege on 2008-03-04
For the developers and others. I have the same issue with a rt2500 pcmcia card. I originally installed Debian unstable and it was slow, then installed Hardy to see if it was better and it is the same. The same router and hardware works full speed under Gutsy.

We I say slow I mean simple pages timing out. The network side works slowly as well, although I can browse my home network.

So, the issue would be not a driver one, but the fundamental wireless network layer. 

Hope this helps someone.

---

### Post by Bridger987 on 2008-03-10
Shameless bump.  ):P

---

### Post by Buster95 on 2008-03-12
Your experiences seem to the same as mine. I read all the threads I could find and unsuccessfully tried every solution I could find over many months, including ndiswrapper.

The only thing that produced any result was to remove all drivers according to kevdogs instructions and to reload a patched driver from [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/).

I also reverted to 7.04, but since it started working, I haven't dared to try 7.10. It may well be OK now.

I now have an unreliable, slow wireless connection, but at least it works most of the time. 

By the way, question raised in message #9 earlier in the thread, asked why the terminal command lshw -C network doesn't display a driver. Nor does mine, but the wireless works (more or less). I assume that the driver for a usb wireless card will not be displayed here.

Cheers

---

### Post by Bridger987 on 2008-03-15
Hmm... that is odd.  But I'm glad that it's not just me that's having this problem.  How would I go about downgrading to 7.04 without wiping my hard drive again?  Worst comes to worst, I can just back things up onto my external HD... But first, how are people's experiences with 7.04 as compared to 7.10 when it comes to wireless?

---

