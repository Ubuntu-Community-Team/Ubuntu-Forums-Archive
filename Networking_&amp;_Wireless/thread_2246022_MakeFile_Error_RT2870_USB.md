---
title: "MakeFile Error RT2870 USB"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by jameslehart on 2014-09-27
Hi i've just installed Ubuntu, i've got a USB wifi card from ebay and the driver for Linux that came with it doesn't seem to install.
I've little knowledge of installing drivers for Ubuntu, i've opened the terminal, extracted the driver folder, naviagated to it and ran

```
sudo make
```

This is the Make response 

```
make -C tools
make[1]: Entering directory `/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools/bin2h
cp -f os/linux/Makefile.6 /home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/Makefile
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable ‘i’ [-Wunused-variable]
  ULONG i;
        ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1121:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:1122:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable ‘macValue’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [LINUX] Error 2
llandudnorepairs@llandudnorepairs-ThinkPad-X100e:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ 

```

I've tried another driver and again i get the same Error 1 and Error 2 message.

when i go for the ```
sudo make install
``` command i get

```
llandudnorepairs@llandudnorepairs-ThinkPad-X100e:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo make install
make -C /home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Usta.ko /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/
install: cannot stat ‘mt7601Usta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/llandudnorepairs/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
make: *** [install] Error 2
llandudnorepairs@llandudnorepairs-ThinkPad-X100e:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ 

```

Its really frustrating, i can't use the built in wifi on my laptop as its not working (doesn't work in linux or windows (power issue)).

Please if anyone could help me i'd really appreciate it, i've had just about enough issue with this laptop as it is, Its a Thinkpad X100e, supposidly designed for Windows 7 but runs slow as hell, i've just recently realised it is a single core processor hence the slow speeds.

---

### Post by jameslehart on 2014-09-30
Bump

Please if anyone could help me, i'd hate to have to revert to windows 7 as it's very slow for this machine. XP is a no go too

---

### Post by steeldriver on 2014-09-30
Those kind of errors usually indicate that the drivers you are trying to build are not compatible with the current kernel - I'd suggest running the wireless info script (should be linked in the stickies) and posting back the results, hopefully one of the wireless gurus will be able to suggest an alternative route for getting your card working

---

