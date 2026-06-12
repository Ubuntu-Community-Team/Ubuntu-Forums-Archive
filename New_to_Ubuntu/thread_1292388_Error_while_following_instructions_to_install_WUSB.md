---
title: "Error while following instructions to install WUSB600N"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by deleyd on 2009-10-15
I was following the instructions at:
How to set up WUSB600N wireless with Ubuntu
[http://ubuntuforums.org/showthread.php?t=1132275](http://ubuntuforums.org/showthread.php?t=1132275)

and got a bunch of errors when I got to Part 2: Installing the drivers, when I ran the sudo make command. Here's the output:

david@david-laptop:~$ **tar -xvvf WUSB600N.tar**
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/common/
-rwxrwxrwx 0/0           51834 2008-09-18 19:59 WUSB600N/common/2870_rtmp_init.c
-rwxrwxrwx 0/0           31495 2008-09-18 20:00 WUSB600N/common/action.c
-rwxrwxrwx 0/0           48774 2008-09-18 20:01 WUSB600N/common/ba_action.c
-rwxrwxrwx 0/0           73713 2008-09-18 20:02 WUSB600N/common/cmm_data.c
-rwxrwxrwx 0/0           29378 2008-09-18 20:03 WUSB600N/common/cmm_data_2870.c
-rwxrwxrwx 0/0          104931 2008-09-18 20:41 WUSB600N/common/cmm_info.c
-rwxrwxrwx 0/0           52319 2008-09-18 20:42 WUSB600N/common/cmm_sanity.c
-rwxrwxrwx 0/0           24813 2008-09-18 20:42 WUSB600N/common/cmm_sync.c
-rwxrwxrwx 0/0           46205 2008-09-25 00:09 WUSB600N/common/cmm_wpa.c
-rwxrwxrwx 0/0           10710 2008-09-18 20:43 WUSB600N/common/dfs.c
-rwxrwxrwx 0/0            5824 2008-09-18 20:43 WUSB600N/common/eeprom.c
-rwxrwxrwx 0/0           45573 2008-09-18 20:43 WUSB600N/common/md5.c
-rwxrwxrwx 0/0          254927 2008-09-25 00:04 WUSB600N/common/mlme.c
-rwxrwxrwx 0/0            4350 2008-09-18 20:45 WUSB600N/common/netif_block.c
-rwxrwxrwx 0/0            8192 2008-09-18 00:55 WUSB600N/common/rt2870.bin
-rwxrwxrwx 0/0          117484 2008-09-18 20:46 WUSB600N/common/rtmp_init.c
-rwxrwxrwx 0/0           40173 2008-09-18 20:46 WUSB600N/common/rtmp_tkip.c
-rwxrwxrwx 0/0           14030 2008-09-18 20:47 WUSB600N/common/rtmp_wep.c
-rwxrwxrwx 0/0           59431 2008-09-18 22:13 WUSB600N/common/rtusb_bulk.c
-rwxrwxrwx 0/0            6826 2008-09-18 22:18 WUSB600N/common/rtusb_data.c
-rwxrwxrwx 0/0           61737 2008-09-18 22:19 WUSB600N/common/rtusb_io.c
-rwxrwxrwx 0/0           47190 2008-09-18 22:20 WUSB600N/common/spectrum.c
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/include/
-rwxrwxrwx 0/0            2200 2008-09-18 22:20 WUSB600N/include/action.h
-rwxrwxrwx 0/0            7216 2008-09-18 22:20 WUSB600N/include/aironet.h
-rwxrwxrwx 0/0           12903 2008-09-18 22:20 WUSB600N/include/ap.h
-rwxrwxrwx 0/0           28679 2008-09-18 22:21 WUSB600N/include/chlist.h
-rwxrwxrwx 0/0            2764 2008-09-18 22:21 WUSB600N/include/dfs.h
-rwxrwxrwx 0/0           51927 2008-09-25 01:37 WUSB600N/include/firmware.h
-rwxrwxrwx 0/0            6313 2008-09-18 22:21 WUSB600N/include/leap.h
-rwxrwxrwx 0/0            3324 2008-09-18 22:21 WUSB600N/include/link_list.h
-rwxrwxrwx 0/0            1836 2008-09-18 22:21 WUSB600N/include/md4.h
-rwxrwxrwx 0/0            3675 2008-09-18 22:22 WUSB600N/include/md5.h
-rwxrwxrwx 0/0           49085 2008-09-18 22:22 WUSB600N/include/mlme.h
-rwxrwxrwx 0/0            2042 2008-09-18 22:22 WUSB600N/include/netif_block.h
-rwxrwxrwx 0/0           40635 2008-09-25 00:03 WUSB600N/include/oid.h
-rwxrwxrwx 0/0           30010 2008-11-05 10:11 WUSB600N/include/rt2870.h
-rwxrwxrwx 0/0           83159 2008-09-18 22:24 WUSB600N/include/rt28xx.h
-rwxrwxrwx 0/0          219257 2008-09-18 22:29 WUSB600N/include/rtmp.h
-rwxrwxrwx 0/0            3714 2008-09-18 22:30 WUSB600N/include/rtmp_ckipmic.h
-rwxrwxrwx 0/0           61493 2008-09-18 22:31 WUSB600N/include/rtmp_def.h
-rwxrwxrwx 0/0            3020 2008-09-18 22:32 WUSB600N/include/rtmp_type.h
-rwxrwxrwx 0/0            7580 2008-09-18 22:24 WUSB600N/include/rt_ate.h
-rwxrwxrwx 0/0            2962 2008-09-18 22:25 WUSB600N/include/rt_config.h
-rwxrwxrwx 0/0           28944 2008-09-18 22:26 WUSB600N/include/rt_linux.h
-rwxrwxrwx 0/0            7936 2008-09-18 22:55 WUSB600N/include/spectrum.h
-rwxrwxrwx 0/0            3270 2008-09-18 22:32 WUSB600N/include/spectrum_def.h
-rwxrwxrwx 0/0            9765 2008-09-25 00:03 WUSB600N/include/wpa.h
-rwxrwxrwx 0/0           10718 2008-09-18 01:06 WUSB600N/iwpriv_usage.txt
-rwxrwxrwx 0/0            5969 2008-09-18 00:55 WUSB600N/Makefile
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/os/
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/os/linux/
-rwxrwxrwx 0/0           43041 2008-09-18 22:33 WUSB600N/os/linux/2870_main_dev.c
-rwxrwxrwx 0/0            7970 2008-11-05 10:10 WUSB600N/os/linux/config.mk
-rwxrwxrwx 0/0            2472 2008-09-18 01:12 WUSB600N/os/linux/Makefile.4
-rwxrwxrwx 0/0            2148 2008-09-18 01:12 WUSB600N/os/linux/Makefile.6
-rwxrwxrwx 0/0               0 2008-09-18 19:57 WUSB600N/os/linux/Module.symvers
-rwxrwxrwx 0/0             106 2008-09-18 23:35 WUSB600N/os/linux/modules.order
-rwxrwxrwx 0/0          181449 2008-09-18 22:38 WUSB600N/os/linux/rt_ate.c
-rwxrwxrwx 0/0           29411 2008-09-18 22:38 WUSB600N/os/linux/rt_linux.c
-rwxrwxrwx 0/0           48271 2008-09-18 22:40 WUSB600N/os/linux/rt_main_dev.c
-rwxrwxrwx 0/0           57525 2008-09-18 22:40 WUSB600N/os/linux/rt_profile.c
-rwxrwxrwx 0/0          256170 2008-09-25 01:28 WUSB600N/os/linux/sta_ioctl.c
-rwxrwxrwx 0/0             867 2008-09-18 23:38 WUSB600N/os/linux/sta_ioctl.c.patch
-rwxrwxrwx 0/0          254862 2008-09-18 23:37 WUSB600N/os/linux/tmp60
-rwxrwxrwx 0/0          254862 2008-09-18 23:37 WUSB600N/os/linux/tmp61
-rwxrwxrwx 0/0           11656 2008-09-18 01:07 WUSB600N/README_STA
-rwxrwxrwx 0/0             734 2008-09-18 01:06 WUSB600N/RT2870STA.dat
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/sta/
-rwxrwxrwx 0/0           44721 2008-09-18 22:42 WUSB600N/sta/aironet.c
-rwxrwxrwx 0/0           72481 2008-09-24 20:13 WUSB600N/sta/assoc.c
-rwxrwxrwx 0/0           18152 2008-09-18 22:46 WUSB600N/sta/auth.c
-rwxrwxrwx 0/0            5932 2008-09-18 22:46 WUSB600N/sta/auth_rsp.c
-rwxrwxrwx 0/0           98376 2008-09-25 00:02 WUSB600N/sta/connect.c
-rwxrwxrwx 0/0           75541 2008-09-18 22:47 WUSB600N/sta/dls.c
-rwxrwxrwx 0/0           72395 2008-09-18 22:49 WUSB600N/sta/rtmp_data.c
-rwxrwxrwx 0/0           13728 2008-09-18 22:50 WUSB600N/sta/sanity.c
-rwxrwxrwx 0/0           61964 2008-09-18 22:51 WUSB600N/sta/sync.c
-rwxrwxrwx 0/0           64403 2008-09-25 00:02 WUSB600N/sta/wpa.c
drwxrwxrwx 0/0               0 2008-11-05 10:08 WUSB600N/tools/
-rwxrwxrwx 0/0           13593 2008-09-25 01:37 WUSB600N/tools/bin2h
-rwxrwxrwx 0/0            6384 2008-09-18 22:52 WUSB600N/tools/bin2h.c
-rwxrwxrwx 0/0              57 2008-09-18 00:55 WUSB600N/tools/Makefile

david@david-laptop:~$ **cd WUSB600N**

david@david-laptop:~/WUSB600N$ **sudo make**
[sudo] password for david:
make -C tools
make[1]: Entering directory `/home/david/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function "main":
bin2h.c:34: error: "FILE" undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: "infile" undeclared (first use in this function)
bin2h.c:34: error: "outfile" undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function "memset"
bin2h.c:49: warning: incompatible implicit declaration of built-in function "printf"
bin2h.c:54: warning: incompatible implicit declaration of built-in function "printf"
bin2h.c:57: warning: incompatible implicit declaration of built-in function "strcat"
bin2h.c:69: error: expected expression before ")" token
bin2h.c:71: warning: incompatible implicit declaration of built-in function "printf"
bin2h.c:76: error: expected expression before ")" token
bin2h.c:78: warning: incompatible implicit declaration of built-in function "printf"
bin2h.c:146: warning: incompatible implicit declaration of built-in function "sprintf"
bin2h.c:155: warning: incompatible implicit declaration of built-in function "exit"
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/david/WUSB600N/tools'
make: *** [build_tools] Error 2
david@david-laptop:~/WUSB600N$

So, what do I do know? (Good with computers, novice with Linux.)

---

### Post by anewguy on 2009-10-16
I don't know if it would make any difference, but did you install the build-essential package before you tried the make?  I would install it then go back and try the make again.

Dave :)

---

### Post by deleyd on 2009-10-16
> **anewguy said:**
> I don't know if it would make any difference, but did you install the build-essential package before you tried the make?  I would install it then go back and try the make again.

Dave :)
What is the "build-essential package"?

---

### Post by anewguy on 2009-10-16
Build-essential is used when building packages.  I'm going to guess you had some way to access the net (hard-wired, perhaps) while trying to build drivers for your USB adapter.  The errors indicate some things needed to build your driver (the "make" is "building" a program).

Also, it looks like you downloaded a tar file to get the driver source.  This doesn't pick up any dependencies that what you downloaded my need,

Assuming you have internet access of some type, use synaptic package manager, search for "build-essential".  If it is not already marked as installed, click it and mark for installation, then apply.  This should download the package and install it.

Once the build-essential package has been installed, go back to the "make" and try again.

Report back any errors.

Dave :)

---

