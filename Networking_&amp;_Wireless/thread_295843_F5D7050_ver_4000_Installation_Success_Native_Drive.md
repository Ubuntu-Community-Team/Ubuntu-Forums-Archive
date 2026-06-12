---
title: "F5D7050 ver 4000 Installation Success Native Drivers"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by FrodoB on 2006-11-08
Please follow the improved documentation of the procedure at:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

The original procedure is left for completeness.

Installing a Belkin F5D7050 ver 4000 Device ID: 050d:705c (Zydas zd1211b chipset)

This procedure also works with the Gigafast WF748-CUI and Airlink101 AWLL3026, both of which have a USB Device ID of:

0ace:1215 ZyDAS

Note: I have only tested this using 128bit (104bit) WEP on Ubuntu 6.10 Edgy Eft.

1. Blacklist the existing zd1211rw driver that is included in Edgy Eft by editing the blacklist file:

$ sudo gedit /etc/modprobe.d/blacklist

add the following to the end of the file:

blacklist zd1211rw

If you have been playing around with ndiswrapper you should blacklist it as well.

2. You will need to install the essential build files to compile the driver:  user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential
Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.) 
 user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
 
or use Synaptic to get the same packages.

3. Download the latest version of the zd1211 drivers from:

[http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/)

The latest at the time I am writing this is: 

zd1211-driver-r83.tgz

4. Extract the archive into you home directory and then change into that directory:

user@ubuntu:~zd1211-driver-r83$ 

5. Edit the Make file and change the line that says ZD1211REV_B=0 to 1:

ZD1211REV_B=1

Save the file.

6. Make the driver with:

$ sudo make install

Note that the build of apdbg.c fails at the end, but this is after the driver is installed. I am not sure what this little program does, but it does not seem to be critical.  By the way it builds on Slackware and Freespire, go figure.

7. Confirm that the :/lib/modules/2.6.17-10-generic/net contains the zd1211b.ko file.

8. Insert your F5D7050 version 4000 device into a usb connector on your machine and verify that you can see it by running lsusb. You should see the device as:

Bus 00X Device 00X: ID 050d:705c Belkin Components 

9. In a terminal window run iwconfig and you should see the device as wlan0.

10. Open the Network setup tool at System -> Administration -> Networking and setup the device.

11. Open a terminal and verify that it is working correctly with iwconfig.

12. You may want to reboot the system and see that everything is still recognized.

If you try it and it works for you please let me know. If I left anything out please let me know as well.

Good Luck,

FrodoB

---

### Post by FrodoB on 2006-11-14
I have now made a improved howto document on the installation of the F5D7050 ver 4000 using the Zydas zd1211 driver. 

The new document is cleaned up and easier to follow.

This new document can be found on the Ubuntu Documentation site here:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Please let me know if any issues that you may encounter with the documentation.

---

### Post by chipr on 2006-11-21
The document calls for installing the *linux-headers* package, which would install to */usr/src/linux-headers-`uname -r`*, not */usr/src/linux-`uname -r`*.

With that change the *make* now runs, but the build fails.

```

chip@coldsnap:/usr/local/src/zd1211-driver-r83$ make
/lib/modules/2.6.17-10-generic/build
/usr/local/src/zd1211-driver-r83
-I/usr/local/src/zd1211-driver-r83/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/local/src/zd1211-driver-r83 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.17-10/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/local/src/zd1211-driver-r83/src/zd1205.o
In file included from /usr/local/src/zd1211-driver-r83/src/zd1205.c:42:
/usr/local/src/zd1211-driver-r83/src/zd1205.h:1332: warning: type qualifiers ignored on function return type
/usr/local/src/zd1211-driver-r83/src/zd1205.h:1279: warning: ‘zd_readl’ declared inline after being called
/usr/local/src/zd1211-driver-r83/src/zd1205.h:1279: warning: previous declaration of ‘zd_readl’ was here
/usr/local/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_validate_frame’:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:2809: warning: unused variable ‘len1’
/usr/local/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205wext_iw_get_stats’:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:4777: error: ‘struct driver_stats’ has no member named ‘iw_stats’
/usr/local/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_translate_scan’:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7183: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘U32’
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7183: warning: unknown conversion type character ‘,’ in format
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7183: warning: spurious trailing ‘%’ in format
/usr/local/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_list_bss’:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7388: warning: format ‘%2d’ expects type ‘int’, but argument 2 has type ‘U32’
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7388: warning: spurious trailing ‘%’ in format
/usr/local/src/zd1211-driver-r83/src/zd1205.c: At top level:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7527: warning: type qualifiers ignored on function return type
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7608: warning: type qualifiers ignored on function return type
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7697: warning: type qualifiers ignored on function return type
/usr/local/src/zd1211-driver-r83/src/zd1205.c:7713: warning: type qualifiers ignored on function return type
/usr/local/src/zd1211-driver-r83/src/zd1205.c: In function ‘CalculateQuality’:
/usr/local/src/zd1211-driver-r83/src/zd1205.c:10074: warning: unused variable ‘rxOffset’
make[2]: *** [/usr/local/src/zd1211-driver-r83/src/zd1205.o] Error 1
make[1]: *** [_module_/usr/local/src/zd1211-driver-r83] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10'
make: *** [all] Error 2
chip@coldsnap:/usr/local/src/zd1211-driver-r83$

```

It looks like the problem is because CONFIG_NET_WIRELESS is not defined.

I'm wondering if you built this with full source installed ... not just headers?

---

### Post by FrodoB on 2006-11-21
I think that you are missing something, from the howto document: (Perhaps you have printed off an earlier version?)

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.) 
 user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

The last statement, linking to the /lib/modules area should solve your issue.

I do seem to remember that the link was missing in an earlier version. Thanks for pointing this out.

---

### Post by chipr on 2006-11-21
FrodoB - it's working now, thanks. I also had some files from a previous attempt that I needed to remove.

---

### Post by FrodoB on 2006-11-22
Excellent, congratuations and enjoy.

---

### Post by euangeleo on 2007-10-05
Thanks for the detail, FrodoB. I came across the documentation you wrote via a google search, but the link to download the source didn't work for me. I kept looking around, and found the project had moved elsewhere. I put a short note at the top of the documentation page for anyone else who comes along, pointing to the Sourceforge site and linuxwireless.org site. This thread is kinda stale now, but just FYI.

---

