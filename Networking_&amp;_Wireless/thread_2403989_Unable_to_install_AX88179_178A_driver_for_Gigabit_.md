---
title: "Unable to install AX88179_178A driver for Gigabit USB 3.0 LAN Network Adapter"
date: 2018-10-18
forum: Networking &amp; Wireless
---

### Post by wiz70 on 2018-10-18
The problem is associated to Ubuntu 18.04.

[SIZE=3][COLOR=#333333][FONT=Verdana]I have 2 debian linux OS laptops. One laptop ( Mint17.3)  uses 3.13.0-156 generic [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]kernel. I downloaded the linux driver from ' [/FONT][/COLOR][www.asix.com.tw/]("http://www.asix.com.tw/")[COLOR=#333333][FONT=Verdana] ' and  [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]complied / installed it on this laptop. The LAN connection was made and[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]ethernet interface worked.[/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Second laptop (Ubuntu 18.04) uses 4.15.0-36 generic kernel. I used the same driver that [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]as installed on first laptop. I made sure build essentials, linux [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]headers, elfutil and libelf packages were install on this laptop before[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]executing "make and make install".  [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]This device doesn't work on the second laptop.   [/FONT][/COLOR][/SIZE]  [COLOR=#333333][FONT=Verdana]Included and attached, are screen shots of the compile/install and listing [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]of dmesg for the usb device.[/FONT][/COLOR] 

[COLOR=#333333][FONT=Verdana][image: compile1.jpg][/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana][image: dmesg1.jpg][/FONT][/COLOR]



[COLOR=#333333][FONT=Verdana]*************[/FONT][/COLOR]
[SIZE=4][COLOR=#333333][FONT=Verdana]&#65532;I did some additional work to install the driver. This time I used[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]'checkinstall' and got the following results .[/FONT][/COLOR][/SIZE]

[COLOR=#333333][FONT=Verdana]This the results of 'checkinstall'[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]******************************[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]**********[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]**** Debian package creation selected ***[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]******************************[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]***********[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: The package name "AX88179_178A_LINUX_DRIVER_v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0_SOURCE"[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]contains[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]upper case[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: letters. dpkg might not like that so I changed[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: them to lower case.[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: The package name "ax88179_178a_linux_driver_v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0_source"[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]contains illegal[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: characters. dpkg might not like that so I changed[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Warning: them to dashes.[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]This package will be built according to these values:[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]0 - Maintainer: [ root@wiz3-Aspire-E5-576 ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]1 - Summary: [ USB3LAN ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]2 - Name: [ ax88179-178a-linux-driver-v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0-source ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]3 - Version: [ 20181008 ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]4 - Release: [ 1 ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]5 - License: [ GPL ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]6 - Group: [ checkinstall ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]7 - Architecture: [ amd64 ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]8 - Source location: [ AX88179_178A_LINUX_DRIVER_v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0_SOURCE ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]9 - Alternate source location: [ ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]10 - Requires: [ ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]11 - Provides: [ ax88179-178a-linux-driver-v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0-source ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]12 - Conflicts: [ ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]13 - Replaces: [ ][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Enter a number to change any of them or press ENTER to continue:[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Installing with make install...[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]========================= Installation results ===========================[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]su -c "cp -v ax88179_178a.ko[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]/lib/modules/4.15.0-36-[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]generic/kernel/drivers/net/usb && /sbin/depmod[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]-a"[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]'ax88179_178a.ko' ->[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]'/lib/modules/4.15.0-36-[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]generic/kernel/drivers/net/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]usb/ax88179_178a.ko'[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]======================== Installation successful ==========================[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Copying files to the temporary directory...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Stripping ELF binaries and libraries...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Compressing man pages...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Building file list...OKKernel modules found. Calling depmod in the[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]postinstall script[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Building Debian package...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Installing Debian package... FAILED![/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** Failed to install the package[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Do you want to see the log file? [y]:[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Selecting previously unselected package[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]ax88179-178a-linux-driver-v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0-source.[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana](Reading database ... 228933 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Preparing to unpack[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana].../ax88179-178a-linux-driver-[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]v1.19.0-source_20181008-1_[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]amd64.deb ...[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Unpacking ax88179-178a-linux-driver-v1.[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]19.0-source (20181008-1) ...[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]dpkg: error processing archive[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]/usr/local/src/AX88179_178A_[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]LINUX_DRIVER_v1.19.0_SOURCE/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]ax88179-178a-linux-driver-[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]v1.19.0-source_20181008-1_[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]amd64.deb (--install):[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]trying to overwrite[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]'/lib/modules/4.15.0-36-[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]generic/kernel/drivers/net/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]usb/ax88179_178a.ko',[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]which is[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]also in package linux-modules-extra-4.15.0-36-[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]generic 4.15.0-36.39[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]/usr/local/src/AX88179_178A_[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]LINUX_DRIVER_v1.19.0_SOURCE/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]ax88179-178a-linux-driver-[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]v1.19.0-source_20181008-1_[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]/var/tmp/tmp.msbax7CC7b/[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]dpkginstall.log (END)[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]*** SIGINT received ***[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Restoring overwritten files from backup...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Cleaning up...OK[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]Bye.



[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]I sent emails to the '[/FONT][/COLOR][EMAIL="Support@asix.com.tw"]Support@asix.com.tw[/EMAIL][COLOR=#333333][FONT=Verdana]' identifying the problem but,[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]they don't respond.[/FONT][/COLOR]

[COLOR=#333333][FONT=Verdana]Any idea on how to fix the problem?????[/FONT][/COLOR]

---

### Post by chili555 on 2018-10-18
```
trying to overwrite
'/lib/modules/4.15.0-36-generic/kernel/drivers/net/usb/ax88179_178a.ko',
which is
also in package linux-modules-extra-4.15.0-36-generic 4.15.0-36.39
```Why are you trying to install this driver in place of the built-in already driver? What problem are you having that you think can be solved by installing a possibly older, possibly no better driver?

---

### Post by wiz70 on 2018-10-18
This what I found in dmesg when adapter was plugged in.

[   20.852031]Bluetooth: RFCOMM TTY layer initialized
[   20.852036]Bluetooth: RFCOMM socket layer initialized
[   20.852041]Bluetooth: RFCOMM ver 1.11
[   28.164259]ip6_tables: (C) 2000-2006 Netfilter Core Team
[  245.943793] usb2-2: new SuperSpeed USB device number 2 using xhci_hcd
[  245.971540] usb2-2: New USB device found, idVendor=0b95, idProduct=1790
[  245.971549] usb2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  245.971556] usb2-2: Product: AX88179
[  245.971562] usb2-2: Manufacturer: ASIX Elec. Corp.
[  245.971567] usb2-2: SerialNumber: 00000000000340
[  246.000938]Lockdown: Loading of unsigned modules is restricted; see mankernel_lockdown.7
wiz3@wiz3-Aspire-E5-576:~$


$ mankernel_lockdown.7
No manual entry forkernel_lockdown.7

I'm still some what of a novice.  I thought the driver needed to be updated and that is why I downloaded the driver from manufacture.  So I did and tried to complie it.  As a result nothing was installed.

But, the following exists on my laptop....      I don't know how to get around the unsigned module restriction.   Open to suggestions on what to do to correct this problem...    Thx.....
    
'/lib/modules/4.15.0-36-generic/kernel/drivers/net/usb/ax88179_178a.ko

---

### Post by chili555 on 2018-10-18
Please see comment #1 here: [https://bugzilla.redhat.com/show_bug.cgi?id=1599197](https://bugzilla.redhat.com/show_bug.cgi?id=1599197)

You could probably also disable secure boot in the BIOS.

---

### Post by wiz70 on 2018-10-20
My laptop is a dual boot system.  When I installed Ubuntu, 'Secure Boot' was disabled.  2 weeks ago, I tried to install a different application.  That required the install of 'linux-modules-extra-xxxxx'.  After the install, I did a update which included a new 'grub' package.  After a reboot, found Bios 'Boot Order' was changed.  I just checked Bios and 'Secure Boot' was enabled.  Disabled 'SecureBoot' and the USB-Ethernet adapter works.   THANKS FOR THE HELP!!!!    SOLVED.....

---

### Post by wiz70 on 2018-10-20
Solved

---

