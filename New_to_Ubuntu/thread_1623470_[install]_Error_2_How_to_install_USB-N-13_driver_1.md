---
title: "[install] Error 2 How to install USB-N-13 driver 10.04"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by dinklebob on 2010-11-16
I know this has question has been answered a million times, but I haven't found anyone running into an [install] Error 2. Basically I'm completely at a loss. Thanks in advance for your help!

Here is the error in question.


dinklebob@Compy:~/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO$ sudo make
[sudo] password for dinklebob: 
make -C tools
make[1]: Entering directory `/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools'
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/crypt_md5.o
In file included from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rt_config.h:99,
                 from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/crypt_md5.c:28:
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:652: error: ‘TX_RING_SIZE’ undeclared here (not in a function)
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:660: error: ‘RX_RING_SIZE’ undeclared here (not in a function)
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:668: error: ‘MGMT_RING_SIZE’ undeclared here (not in a function)
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:724: error: ‘NUM_OF_TX_RING’ undeclared here (not in a function)
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:2573: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:2840: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:3390: error: expected specifier-qualifier-list before ‘RT28XX_RXD_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:4166: error: expected declaration specifiers or ‘...’ before ‘INT_SOURCE_CSR_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:4246: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:4266: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:4272: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
In file included from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rt_config.h:99,
                 from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/crypt_md5.c:28:
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:6846: error: expected declaration specifiers or ‘...’ before ‘PRXWI_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:6850: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rtmp.h:7124: error: expected declaration specifiers or ‘...’ before ‘RTMP_INF_TYPE’
In file included from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/rt_config.h:100,
                 from /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/crypt_md5.c:28:
/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/include/ap.h:91: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
make[2]: *** [/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/crypt_md5.o] Error 1
make[1]: *** [_module_/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [LINUX] Error 2
dinklebob@Compy:~/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO$ sudo make install
make -C /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux'
rm -rf /etc/Wireless/RTSTA
mkdir /etc/Wireless/RTSTA
cp /home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/RTSTA.dat /etc/Wireless/RTSTA/.
cp: cannot stat `/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/RTSTA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/dinklebob/Drivers/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux'
make: *** [install] Error 2

---

### Post by Hippytaff on 2010-11-17
Hi
 
I'm assuming your trying to install a ralink driver for a d-link usb wirelss donge? if so this might be of some use
[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)
 
Post back, if that doesn't help, you might need to look into ndiswrapper and isung the windows xp driver...
 
:-)

---

### Post by dinklebob on 2010-11-17
I've looked at that thread before and I just got error after error. Also, I'm currently using another wireless adapter and I'm using ndiswrapper. I installed the windows drivers, but nothing came up! It even recognized my hardware (although the device itself never lit up)

---

### Post by Hippytaff on 2010-11-18
In that case you might want to look into usb_modeswitch. It may be that the device looks like a usb storage device. Mode switch will change the mode to wireless usb adapter :-)

---

### Post by dinklebob on 2010-11-20
*sigh* I'm getting a huge list of 
"usb_modeswitch.c:1174: error: dereferencing pointer to incomplete type"
when I try to install that program. It looks like Ubuntu hates me with a passion. Oh well, I guess my parents will get the new adapter after all.

---

### Post by Hippytaff on 2010-11-20
first of all - ubuntu doesn't hate you

most of the people here on the forum love you (yes they do!!!)

Have you looked into using a windows xp driver with ndiswrapper?

---

### Post by dinklebob on 2010-11-20
I just meant the OS itself seems more than a little bit temperamental towards me.

I am currently using ndiswrapper for my current adapter (Westell 802.11g) and I installed the XP, Vista, and 7 drivers from the disk (at separate times, of course). I couldn't get any of them to work. It said that the driver was installed and that the hardware was in place, but my network connections manager didn't show anything. I suppose the only thing I didn't try (when it comes to ndiswrapper) was uninstalling the driver for the Westell so that the ASUS drivers would be the only ones installed. It works fine now, but we may be upgrading to a N system soon so I was hoping I could get the USB-N13 802.11n to work.

Just for grins and giggles, let me attach the readme for the official Linux driver that came bundled with the new adapter (the one giving me all the errors). Perhaps you'll be able to spot something that I might have missed or done wrong.

---

### Post by Hippytaff on 2010-11-21
So following that doesn't work?

---

### Post by dinklebob on 2010-11-22
Following that is what is giving me all of these error messages.

---

### Post by 3rdalbum on 2010-11-22
Hang on a second, I think this driver is in Ubuntu already, but conflicts with a similar driver. If you blacklist the bad driver, the device should work. Please PM me and when I get home I will be able to give you the information on how to do the blacklisting. My device at home is the same as yours.

---

### Post by Hippytaff on 2010-11-23
Blacklisting was going  to be my next step - but looks as though 3rdalbum is better place to assitsti you with this :-)

---

### Post by dinklebob on 2010-11-23
Well I haven't quite gotten a response from 3rdalbum yet, so if anyone else has any suggestion I'm highly open to it.

---

