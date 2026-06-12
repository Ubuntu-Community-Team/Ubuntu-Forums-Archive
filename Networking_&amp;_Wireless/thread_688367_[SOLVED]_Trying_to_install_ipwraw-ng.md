---
title: "[SOLVED] Trying to install ipwraw-ng"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by NovaAesa on 2008-02-05
I'm trying to install ipwraw-ng for my wireless chipset Intel Pro/Wireless 3945ABG following the instructions [here]("http://www.aircrack-ng.org/doku.php?id=ipw3945"). However, I'm pretty sure it didn't work (there was lots of errors, and later on in the my explorations with aircrack-ng things didn't go as planned). If someone could look through my terminal output and tell me what I'm doing wrong, that would be excellent xD

```

ps@inspiron:~/Desktop/ipwraw-ng$ ls
ap-beacon            GIT_SHA1  iwlwifi_hw.h  README.ipwraw     snapshot
CHANGELOG.ipwraw-ng  INSTALL   kcompat       README.ipwraw-ng  status
CHANGES              in-tree   LICENSE       remove-old        ucode
config               ipwraw.c  LICENSE.GPL   scripts           util
dvals                ipwraw.h  load          set_channel
FILES                ISSUES    Makefile      set_power
ps@inspiron:~/Desktop/ipwraw-ng$ make
make -C /lib/modules/2.6.22-14-generic/build M=/home/ps/Desktop/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ps/Desktop/ipwraw-ng/ipwraw.o
/home/ps/Desktop/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/ps/Desktop/ipwraw-ng/ipwraw.c:8737: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ps/Desktop/ipwraw-ng/ipwraw.mod.o
  LD [M]  /home/ps/Desktop/ipwraw-ng/ipwraw.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Entering directory `/home/ps/Desktop/ipwraw-ng/util'
gcc -I/lib/modules/2.6.22-14-generic/build/include -Wall -c -o wifi_tx.o wifi_tx.c
wifi_tx.c:41:23: error: sys/types.h: No such file or directory
wifi_tx.c:42:22: error: sys/stat.h: No such file or directory
wifi_tx.c:43:22: error: sys/time.h: No such file or directory
wifi_tx.c:44:24: error: sys/socket.h: No such file or directory
wifi_tx.c:45:23: error: sys/ioctl.h: No such file or directory
wifi_tx.c:46:22: error: sys/wait.h: No such file or directory
wifi_tx.c:60:24: error: netinet/in.h: No such file or directory
wifi_tx.c:62:20: error: dirent.h: No such file or directory
wifi_tx.c:63:20: error: stdlib.h: No such file or directory
wifi_tx.c:64:19: error: stdio.h: No such file or directory
wifi_tx.c:65:20: error: signal.h: No such file or directory
wifi_tx.c:66:19: error: fcntl.h: No such file or directory
wifi_tx.c:67:20: error: string.h: No such file or directory
wifi_tx.c:68:19: error: errno.h: No such file or directory
wifi_tx.c:69:20: error: unistd.h: No such file or directory
wifi_tx.c:70:18: error: math.h: No such file or directory
wifi_tx.c:71:19: error: ctype.h: No such file or directory
wifi_tx.c: In function ‘usage’:
wifi_tx.c:286: warning: implicit declaration of function ‘fprintf’
wifi_tx.c:286: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:286: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:286: error: (Each undeclared identifier is reported only once
wifi_tx.c:286: error: for each function it appears in.)
wifi_tx.c:289: error: ‘stdout’ undeclared (first use in this function)
wifi_tx.c: In function ‘param_check’:
wifi_tx.c:349: warning: implicit declaration of function ‘strlen’
wifi_tx.c:349: warning: incompatible implicit declaration of built-in function ‘strlen’
wifi_tx.c:350: warning: implicit declaration of function ‘strncmp’
wifi_tx.c: In function ‘version’:
wifi_tx.c:365: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:365: error: ‘stdout’ undeclared (first use in this function)
wifi_tx.c: In function ‘init_radiotap’:
wifi_tx.c:374: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:374: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c: In function ‘init_ieee80211_hdr_3addr’:
wifi_tx.c:416: warning: implicit declaration of function ‘memcpy’
wifi_tx.c:416: warning: incompatible implicit declaration of built-in function ‘memcpy’
wifi_tx.c: In function ‘init_beacon’:
wifi_tx.c:423: error: storage size of ‘tv’ isn’t known
wifi_tx.c:426: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:426: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:431: warning: implicit declaration of function ‘gettimeofday’
wifi_tx.c:438: warning: implicit declaration of function ‘rand’
wifi_tx.c:442: warning: implicit declaration of function ‘printf’
wifi_tx.c:442: warning: incompatible implicit declaration of built-in function ‘printf’
wifi_tx.c:423: warning: unused variable ‘tv’
wifi_tx.c: In function ‘init_data’:
wifi_tx.c:462: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:462: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c: In function ‘init_csa’:
wifi_tx.c:526: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:526: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c: In function ‘init_deauth’:
wifi_tx.c:559: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:559: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c: In function ‘set_iface_flags’:
wifi_tx.c:576: warning: implicit declaration of function ‘socket’
wifi_tx.c:576: error: ‘SOCK_DGRAM’ undeclared (first use in this function)
wifi_tx.c:578: error: ‘errno’ undeclared (first use in this function)
wifi_tx.c:579: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:579: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:580: warning: implicit declaration of function ‘strerror’
wifi_tx.c:580: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:585: warning: implicit declaration of function ‘memset’
wifi_tx.c:585: warning: incompatible implicit declaration of built-in function ‘memset’
wifi_tx.c:586: warning: implicit declaration of function ‘strncpy’
wifi_tx.c:586: warning: incompatible implicit declaration of built-in function ‘strncpy’
wifi_tx.c:588: warning: implicit declaration of function ‘ioctl’
wifi_tx.c:591: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:592: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:594: warning: implicit declaration of function ‘close’
wifi_tx.c: In function ‘get_iface_flags’:
wifi_tx.c:610: error: ‘SOCK_DGRAM’ undeclared (first use in this function)
wifi_tx.c:612: error: ‘errno’ undeclared (first use in this function)
wifi_tx.c:613: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:613: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:614: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:619: warning: incompatible implicit declaration of built-in function ‘memset’
wifi_tx.c:620: warning: incompatible implicit declaration of built-in function ‘strncpy’
wifi_tx.c:624: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:625: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c: In function ‘open_iface’:
wifi_tx.c:643: warning: implicit declaration of function ‘htons’
wifi_tx.c:650: error: ‘socklen_t’ undeclared (first use in this function)
wifi_tx.c:650: error: expected ‘;’ before ‘err_len’
wifi_tx.c:659: warning: incompatible implicit declaration of built-in function ‘strncpy’
wifi_tx.c:663: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:663: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:665: error: ‘errno’ undeclared (first use in this function)
wifi_tx.c:665: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:671: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:677: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:677: error: ‘stdout’ undeclared (first use in this function)
wifi_tx.c:684: warning: format ‘%s’ expects type ‘char *’, but argument 5 has type ‘int’
wifi_tx.c:691: error: ‘SOCK_RAW’ undeclared (first use in this function)
wifi_tx.c:693: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:694: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:699: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:700: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:707: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:710: warning: implicit declaration of function ‘bind’
wifi_tx.c:713: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:718: warning: implicit declaration of function ‘getsockopt’
wifi_tx.c:718: error: ‘err_len’ undeclared (first use in this function)
wifi_tx.c:720: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c: In function ‘close_iface’:
wifi_tx.c:738: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:738: error: ‘stdout’ undeclared (first use in this function)
wifi_tx.c:742: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:745: error: ‘errno’ undeclared (first use in this function)
wifi_tx.c:745: warning: format ‘%s’ expects type ‘char *’, but argument 5 has type ‘int’
wifi_tx.c: In function ‘send_frame’:
wifi_tx.c:763: warning: implicit declaration of function ‘send’
wifi_tx.c:768: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:768: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:769: error: ‘errno’ undeclared (first use in this function)
wifi_tx.c:770: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
wifi_tx.c:775: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c: In function ‘main’:
wifi_tx.c:794: error: storage size of ‘tv’ isn’t known
wifi_tx.c:797: warning: implicit declaration of function ‘srand’
wifi_tx.c:799: warning: incompatible implicit declaration of built-in function ‘memset’
wifi_tx.c:818: warning: implicit declaration of function ‘strdup’
wifi_tx.c:818: warning: incompatible implicit declaration of built-in function ‘strdup’
wifi_tx.c:836: warning: implicit declaration of function ‘strtol’
wifi_tx.c:938: warning: incompatible implicit declaration of built-in function ‘strdup’
wifi_tx.c:948: warning: incompatible implicit declaration of built-in function ‘fprintf’
wifi_tx.c:948: error: ‘stderr’ undeclared (first use in this function)
wifi_tx.c:794: warning: unused variable ‘tv’
make[1]: *** [wifi_tx.o] Error 1
make[1]: Leaving directory `/home/ps/Desktop/ipwraw-ng/util'
make: *** [utils] Error 2
ps@inspiron:~/Desktop/ipwraw-ng$ sudo make install
[sudo] password for ps:
Installing to /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/...-e done

-e *** WARNING: Couldn't find /lib/firmware/iwlwifi-3945.ucode! ***
Don't forget to copy firmware to your hotplug's firmware directory
-e and have the hotplug tools in place.

You can install the firmware using
-e      make install_ucode
-e 
Please see the README.ipwraw for information on regulatory compliance.

-e You can load the module with
        modprobe ipwraw
ps@inspiron:~/Desktop/ipwraw-ng$ sudo make install_ucode
Installing ucode in /lib/firmware ...-e done

ps@inspiron:~/Desktop/ipwraw-ng$ echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw
blacklist ipwraw
ps@inspiron:~/Desktop/ipwraw-ng$ sudo depmod -ae
ps@inspiron:~/Desktop/ipwraw-ng$ sudo modprobe -r ipw3945
ps@inspiron:~/Desktop/ipwraw-ng$ sudo modprobe ipwraw
ps@inspiron:~/Desktop/ipwraw-ng$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

```

I'm doing this for educational purposes by the way, I don't intend on stealing people's Internet, that would just be mean.

---

### Post by h-kan on 2008-02-05
I was trying to get injection working with that card for weeks now and yesterday i made it :)

To bad i didnt wrote a how to on it :(

I will try to help you as much as i can... but im not sure if its right though so try it on you own risk... 

My researches tells me that the ipw3945 or nowdays more used iwl3945 driver dont support packet injection no matter what you read in other posts...  

But there is a driver called ipwraw-ng that are used on the the spanish live-cd wifiway-0.8
that can be download here 

Before you try installing this driver from this page [http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945)

you should try to download this package 

Proberly you will get alot of error messeges under the installation... 

I managed to solve that by copy some files from the scripts folder by hand...

as root copy following files to /usr/sbin

athenable
b43enable
athload
b43load
madwifi-unload

you proberly also have to do this by hand

mkdir -p /usr/lib/compat-wireless/

and than copy modlib.sh from the script folder there

Than try to run make and make install as root and se if that works...

if it works than install the ipwraw-ng and now it will work if I got it right....

---

### Post by NovaAesa on 2008-02-05
Thank you, I try this and post back with the results (for anyone else who might want to try this).

---

### Post by stairwayoflight on 2008-02-05
Nova,

To build the drivers you need certain packages. 'build-essential' will give you some needed tools, perhaps you have that installed but not kernel headers?

For example, a standard way to have a 386 kernel would be to install 'linux-386' from synaptic. That doesn't include the headers, which can be installed with 'linux-headers-386'. The important thing is tracking down the right headers for your kernel.

If you have this stuff installed, the first driver you mentioned should build ok methinks.

---

### Post by NovaAesa on 2008-02-05
> **stairwayoflight said:**
> Nova,

To build the drivers you need certain packages. 'build-essential' will give you some needed tools, perhaps you have that installed but not kernel headers?

For example, a standard way to have a 386 kernel would be to install 'linux-386' from synaptic. That doesn't include the headers, which can be installed with 'linux-headers-386'. The important thing is tracking down the right headers for your kernel.

If you have this stuff installed, the first driver you mentioned should build ok methinks.
I am currently installing build-essential. I haven't done anything extra to install kernel heads though. Do you know of a way to:

1) Check if kernel headers are installed
2) If they aren't installed, which command should I run? Would ```
sudo apt-get install linux-headers-386
``` do it?

EDIT: I am running 64 bit Gutsy, so I guess linux-headers-386 isn't what I need.
EDIT2: I just noticed some updates that need doing. They are 'linux-headers-2.6.22-14', 'linux-headers-2.6.22-14-generic' and 'linux-image-2.6.22-14-generic'. Are these what you are talking about?

---

### Post by NovaAesa on 2008-02-07
Okay, so I installed build-essential and then tried the steps that I did initially. It worked a charm xD

I guess I must have already had the headers though.

Thank you for your replies!

---

### Post by stairwayoflight on 2008-02-07
No problem!

Oh, and if I remember correctly, the command to install the correct headers for the currently-running kernel is:
```
sudo aptitude install linux-headers-`uname -r`
```
This is a one-liner in your bash shell, and the backticks (upper left of a US keyboard) indicate code to be run. The output of `uname -r` is then substituted into the command automagically.

Good luck!

EDIT: Yes, it seems you have kernel headers installed, and the update software is asking you to update them to a new version along with the rest of your kernel. Updating is a good idea, you may need to recompile the drivers you build from source though.

---

