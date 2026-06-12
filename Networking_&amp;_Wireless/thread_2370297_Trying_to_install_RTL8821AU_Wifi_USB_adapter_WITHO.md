---
title: "Trying to install RTL8821AU Wifi USB adapter WITHOUT INTERNET"
date: 2017-09-01
forum: Networking &amp; Wireless
---

### Post by chahatupreti on 2017-09-01
Hi, I am a complete beginner and I am trying to install the above mentioned Wifi adapter (model - EP-DB1607 provided by EDUP) on a new Ubuntu 17.04 system which DOES NOT have internet connection. I got the driver for it online here ([http://www.szedup.com/support/driver-download/ep-db1607-driver/](http://www.szedup.com/support/driver-download/ep-db1607-driver/)), although it was for Linux as there was nothing for Ubuntu. I ran the install.sh file provided within it on the terminal and received the following error - 


```
scripts/Makefile.build:294: recipe for target '/home/campbell_lab/Public/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' failed 
make[2]: *** [/home/campbell_lab/Public/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o] Error 1 
Makefile:1524: recipe for target '_module_/home/campbell_lab/Public/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed 
make[1]: *** [_module_/home/campbell_lab/Public/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51] Error 2 
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-19-generic' 
Makefile:1551: recipe for target 'modules' failed 
make: *** [modules] Error 2 
################################################## Compile make driver error: 2 
Please check error Mesg
```

And here is the output of lsusb - 

```
root@ZCampbell-MS-7A38:/home/campbell_lab/Public/linux# lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```



[I]It was quite difficult to get these output here, as the computer with this problem is not online!

[/I]So, what should i do? Any help would be great!

---

### Post by praseodym on 2017-09-02
Use the dkms package:

[https://packages.ubuntu.com/zesty/rtl8812au-dkms](https://packages.ubuntu.com/zesty/rtl8812au-dkms)

---

### Post by chahatupreti on 2017-09-04
Hi,

Thank you so much for your response. I downloaded the package from the site you mentioned, and tried to install it as follows (I followed the advice mentioned here - [https://unix.stackexchange.com/a/159114](https://unix.stackexchange.com/a/159114)) - 

```
root@ZCampbell-MS-7A38:/home/campbell_lab/Public/linux# sudo dpkg -i /home/campbell_lab/Public/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu5_all.deb

Selecting previously unselected package rtl8812au-dkms.
(Reading database ... 168830 files and directories currently installed.)
Preparing to unpack .../rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu5_all.deb ...
Unpacking rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu5) ...
dpkg: dependency problems prevent configuration of rtl8812au-dkms:
 rtl8812au-dkms depends on dkms (>= 2.1.0.0); however:
  Package dkms is not installed.


dpkg: error processing package rtl8812au-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtl8812au-dkms
```

Then I ran the second command - 

```

root@ZCampbell-MS-7A38:/home/campbell_lab/Public/linux# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  rtl8812au-dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 8,904 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 169203 files and directories currently installed.)
Removing rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu5) ...
root@ZCampbell-MS-7A38:/home/campbell_lab/Public/linux# 



```

But it does not look like the WiFi has been set up. Am I doing something wrong?

---

### Post by chahatupreti on 2017-09-04
PROBLEM SOLVED.

I installed module-init-tools and dmks, and them installed the rtl package you mentioned before, restarted the system, and it started detecting WiFi connections!

Thanks!

---

### Post by jeremy31 on 2017-09-04
Wait until a kernel update to mark as solved as a bug might still exist in rtl8812au-dkms

---

### Post by chahatupreti on 2017-09-04
1. what is a kernel update?
2. how would I know when there is one?

Thanks!

---

