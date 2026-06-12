---
title: "Realtek USB driver installation"
date: 2018-10-26
forum: Networking &amp; Wireless
---

### Post by n2te on 2018-10-26
Can someone direct me to a page that outlines the stepwise installation procedure of installing the driver for a Realtek rtl8811CU wireless USB WiFi dongle. The result from a lsusb command indicates a hardware ID=0bda:c881  So the system sees the hardware on the USB bus. As I have zero experience installing Linux drivers and producing make files and compiling files for installation I'm in need of, essentially, a stepwise instruction set intended for a novice user for completing this driver installation. 

I've tried a few of the commands that I have found online that seem to address what I'm trying to accomplish but in all cases I encounter error messages that, unfortunately due to my level of Linux experience, I do not understand nor know how to correct. And none of the solutions online match my chipset model.  I'm running Ubuntu 18.04 which has preformed very well for me. Having been a Windows user for many years, this is quite the learning experience. Suggestions appreciated. Thanx.

---

### Post by chili555 on 2018-10-27
May we just have a look at a few details? From the terminal:```
lsusb
uname -r
```Post the result in your reply.


----------

Note to Chili: possibly: [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

---

### Post by n2te on 2018-10-27
ed@EdLinux3:~$ lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0bda:c811 Realtek Semiconductor Corp.** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ed@EdLinux3:~$ uname -r
**4.19.0-041900-generic**

---

### Post by n2te on 2018-10-29
No progress yet. 

~ I'm noticing in many internet related posts that users are advising to go to "System Settings", "Additional Drivers" and that I "Activate" the driver and the OS will automatically install the proprietary driver. In my case that would be the Realtek WiFi USB dongle driver. However when I go to that Systems Settings Additional Drivers page the field is blank and only says, "No additional drivers available". However, I DO have the drivers. Why aren't they "available"? What does "available" mean? If the lsusb command sees the hardware, how is the connection made from that visibility to this sys settings page? 

~ Read thru this post which looks quite complicated: [https://ubuntuforums.org/showthread.php?t=2378849](https://ubuntuforums.org/showthread.php?t=2378849)

~ I've tried disconnecting my wired ethernet cable and rebooting 18.04 wth the USB dongle connected but nothing happens. (no msg's or installations)

~ Another posting advised running the following command:
   sudo apt-get install rtl8811cu-dkms
Executing that command resulted in an error:
   E: Unable to locate package rtl8811cu-dkms

~ Another posting advises the following: (#855668)
   cd to my USB WiFi drivers folder.
then
   make clean
   make
   sudo make install

The "make clean" command appears to do something with no errors. When invoking the "make" command it returns all kinds of errors:
/bin/sh: 1: cc: not found
(standard_in) 1: syntax error
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-041900-generic/build M=/home/ed/Downloads/rtl8821CU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.19.0-041900-generic'
arch/x86/Makefile:150: CONFIG_X86_X32 enabled but no binutils support
./scripts/gcc-version.sh: line 26: gcc: command not found
./scripts/gcc-version.sh: line 27: gcc: command not found
Makefile:960: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
make[1]: gcc: Command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
make[1]: gcc: Command not found
/bin/sh: 1: gcc: not found
(standard_in) 1: syntax error
  CC [M]  /home/ed/Downloads/rtl8821CU/core/rtw_cmd.o
/bin/sh: 1: gcc: not found
scripts/Makefile.build:305: recipe for target '/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o' failed
make[2]: *** [/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o] Error 127
Makefile:1517: recipe for target '_module_/home/ed/Downloads/rtl8821CU' failed
make[1]: *** [_module_/home/ed/Downloads/rtl8821CU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.19.0-041900-generic'
Makefile:1893: recipe for target 'modules' failed
make: *** [modules] Error 2

It appears to have a problem with a "gcc" command. Would this be the correct procedure if there was no error with the gcc command?

~ I noticed that the model of my realtek device in the lsusb command doesn't match the model number listed in my Linux drivers folder. Am I trying to load a non-existent driver and should be searching for a different named driver?

~ Has anyone developed an utility that automatically takes the headache of installing such uncooperative drivers and turned it into a simple task?

Still trying ... onward ... comments, help, guidance, assistance, suggestions appreciated please. ...

---

### Post by praseodym on 2018-10-29
Use the regular kernel, not the mainline kernel

---

### Post by n2te on 2018-10-29
Thank you for your reply. Unfortunately (and my apologies) with my limited Linux experience, I don't know how to use a "regular kernel" nor how to use it in conjunction with installing this driver. If you could provide me with the actual sequence order of terminal commands that I need to specify the "regular" kernel and then the order of commands to make, compile, and install that would be great. Thanks!

---

### Post by n2te on 2018-10-29
I have installed the following:
sudo apt-get install gcc
sudo apt-get install build-essentials
I figured for sure the missing 'gcc' command was the missing link. But no such luck.

I then invoked a 'make' that provided the following output:

~/Downloads/rtl8821CU$ [COLOR=#800080]**make clean**[/COLOR]
#make -C /lib/modules/4.19.0-041900-generic/build M=/home/ed/Downloads/rtl8821CU clean
cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions

ed@EdLinux3:~/Downloads/rtl8821CU$ [COLOR=#800080]**make**[/COLOR]
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-041900-generic/build M=/home/ed/Downloads/rtl8821CU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.19.0-041900-generic'
  CC [M]  /home/ed/Downloads/rtl8821CU/core/rtw_cmd.o
In file included from /home/ed/Downloads/rtl8821CU/include/osdep_service.h:47:0,
                 from /home/ed/Downloads/rtl8821CU/include/drv_types.h:32,
                 from /home/ed/Downloads/rtl8821CU/core/rtw_cmd.c:22:
/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
[COLOR=#ff0000]/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h:295:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h:296:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);[/COLOR]
  ^~~~~~~~~~
  _init_timer
In file included from /home/ed/Downloads/rtl8821CU/include/drv_types.h:35:0,
                 from /home/ed/Downloads/rtl8821CU/core/rtw_cmd.c:22:
/home/ed/Downloads/rtl8821CU/include/wifi.h: At top level:
/home/ed/Downloads/rtl8821CU/include/wifi.h:1019:0: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from /home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h:86:0,
                 from /home/ed/Downloads/rtl8821CU/include/osdep_service.h:47,
                 from /home/ed/Downloads/rtl8821CU/include/drv_types.h:32,
                 from /home/ed/Downloads/rtl8821CU/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1442:0: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
[COLOR=#ff0000]cc1: some warnings being treated as errors
scripts/Makefile.build:305: recipe for target '/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o' failed
make[2]: *** [/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o] Error 1
Makefile:1517: recipe for target '_module_/home/ed/Downloads/rtl8821CU' failed
make[1]: *** [_module_/home/ed/Downloads/rtl8821CU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.19.0-041900-generic'
[/COLOR][I][COLOR=#ff0000]Makefile:1893: recipe for target 'modules' failed
make: *** [modules] Error 2
[/COLOR][/I]
ed@EdLinux3:~/Downloads/rtl8821CU$ [COLOR=#800080]**sudo make install**[/COLOR]
install -p -m 644 8821cu.ko  /lib/modules/4.19.0-041900-generic/kernel/drivers/net/wireless/
install: cannot stat '8821cu.ko': No such file or directory
***[COLOR=#ff0000][/COLOR]***[I][COLOR=#ff0000]Makefile:1899: recipe for target 'install' failed
make: *** [install] Error 1[/COLOR][/I][B][I][COLOR=#ff0000]
[/COLOR][/I][/B]
Any suggestions what's next?

---

### Post by chili555 on 2018-10-29
> **n2te said:**
> Thank you for your reply. Unfortunately (and my apologies) with my limited Linux experience, I don't know how to use a "regular kernel" nor how to use it in conjunction with installing this driver. If you could provide me with the actual sequence order of terminal commands that I need to specify the "regular" kernel and then the order of commands to make, compile, and install that would be great. Thanks!It appears that you installed kernel version 4.19 in a hope to make progress here:> make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/[COLOR="#FF0000"]4.19.0-041900-generic[/COLOR]/build M=/home/ed/Downloads/rtl8821CU modulesReboot; interrupt the boot process to get to the GRUB menu, select Advanced Options and boot into a mainline Ubuntu kernel, likely 4.18.0-10-generic if you are running Ubuntu 18.10 or 4.15.0-3xx if you are running Ubuntu 18.04. [http://tipsonubuntu.com/wp-content/uploads/2015/03/grub-advanced.jpg](http://tipsonubuntu.com/wp-content/uploads/2015/03/grub-advanced.jpg)

The git I referenced above builds with a few warnings but no errors in my 4.18 system. I've confirmed that the driver does cover your device:```

$ modinfo 8821cu.ko | grep C811
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]C811[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin*
```After you boot into the earlier kernel, make clean, make and sudo make install and let us hear the result.

For the benefit of you and the searchers, "~ I'm noticing in many internet related posts that users are advising to go to "System Settings", "Additional Drivers" and that I "Activate" the driver and the OS will automatically install the proprietary driver." If and only if your device is a Broadcom.

You and most Linux newbies probably don't realize that Broadcom drivers are prorietary; that is, not open source, not reviewable by ordinary users and certainly not revisable.

On the other hand, the Realtek driver I refer to above is open source. You and I may see and change the code all we want. Here is a partial copy and paste from the git I referenced above. > 
/******************************************************************************
 *
 * Copyright(c) 2007 - 2011 Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
 * published by the Free Software Foundation.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
 * FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
 * more details.
 *
 * You should have received a copy of the GNU General Public License along with
 * this program; if not, write to the Free Software Foundation, Inc.,
 * 51 Franklin Street, Fifth Floor, Boston, MA 02110, USA
 *
 *
 ******************************************************************************/
#define _HCI_INTF_C_

#include <drv_types.h>
#include <hal_data.h>

#include <platform_ops.h>

#ifndef CONFIG_USB_HCI
#error "CONFIG_USB_HCI shall be on!\n"
#endif

<snip>

Is short, Additional Drivers did not install a proprietary driver because none is available.

---

### Post by n2te on 2018-10-29
Thank you. Great information and much appreciated.  
I'm assuming that the make ARCH=x86........... operation is executed first and then a reboot. However that command appears to report errors. What did I do incorrectly? (thank you so much for your patience with this Linux newbie.)

ed@EdLinux3:~$ **make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-041900-generic/build M=/home/ed/Downloads/rtl8821CU modules** 
make: Entering directory '/usr/src/linux-headers-4.19.0-041900-generic'
[COLOR=#ff0000]/home/ed/Downloads/rtl8821CU/Makefile:820: /usr/src/linux-headers-4.19.0-041900-generic/rtl8821c.mk: No such file or directory[/COLOR]
[COLOR=#ff0000]make[1]: *** No rule to make target '/usr/src/linux-headers-4.19.0-041900-generic/rtl8821c.mk'.  **Stop**.
Makefile:1517: recipe for target '_module_/home/ed/Downloads/rtl8821CU' **failed**
make: *** [_module_/home/ed/Downloads/rtl8821CU] Error 2[/COLOR]
make: Leaving directory '/usr/src/linux-headers-4.19.0-041900-generic'

---

### Post by chili555 on 2018-10-29
> make: Entering directory '/usr/src/linux-headers-[COLOR="#FF0000"]4.19.0-041900-[/COLOR]generic'You still have not booted into an earlier kernel. You rebooted right back to the same not-working kernel.

Reboot into the earlier official kernel. Confirm with:```
uname -r
```*While still booted into that kernel*, do:```
cd  ~/Downloads/rtl8821CU
make clean
make
sudo make install
sudo modprobe 8821cu
```> 
I'm assuming that the make ARCH=x86........... operation is executed first and then a reboot. 
Incorrect.

---

### Post by n2te on 2018-10-29
Almost... we're getting close... 

ed@EdLinux3:~$ **uname -r**
[COLOR=#008000]4.15.0-38-generic[/COLOR]

ed@EdLinux3:~/Downloads/rtl8821CU$ **make clean**
#make -C /lib/modules/4.15.0-38-generic/build M=/home/ed/Downloads/rtl8821CU clean
cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions

ed@EdLinux3:~/Downloads/rtl8821CU$ **make**
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-38-generic/build M=/home/ed/Downloads/rtl8821CU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
  CC [M]  /home/ed/Downloads/rtl8821CU/core/rtw_cmd.o
In file included from /home/ed/Downloads/rtl8821CU/include/osdep_service.h:47:0,
                 from /home/ed/Downloads/rtl8821CU/include/drv_types.h:32,
                 from /home/ed/Downloads/rtl8821CU/core/rtw_cmd.c:22:
/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h:295:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/ed/Downloads/rtl8821CU/include/osdep_service_linux.h:296:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/ed/Downloads/rtl8821CU/include/drv_types.h:32:0,
                 from /home/ed/Downloads/rtl8821CU/core/rtw_cmd.c:22:
/home/ed/Downloads/rtl8821CU/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/ed/Downloads/rtl8821CU/include/osdep_service.h:363:2: [COLOR=#ff0000]error[/COLOR]: implicit declaration of function &#8216;allow_signal&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/home/ed/Downloads/rtl8821CU/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/home/ed/Downloads/rtl8821CU/include/osdep_service.h:385:6: [COLOR=#ff0000]error[/COLOR]: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
  if (signal_pending(current))
      ^~~~~~~~~~~~~~
      timer_pending
/home/ed/Downloads/rtl8821CU/include/osdep_service.h:386:3: [COLOR=#ff0000]error[/COLOR]: implicit declaration of function &#8216;flush_signals&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o' [COLOR=#ff0000]failed[/COLOR]
make[2]: *** [/home/ed/Downloads/rtl8821CU/core/rtw_cmd.o] [COLOR=#ff0000]Error 1[/COLOR]
Makefile:1551: recipe for target '_module_/home/ed/Downloads/rtl8821CU' [COLOR=#ff0000]failed[/COLOR]
make[1]: *** [_module_/home/ed/Downloads/rtl8821CU] [COLOR=#ff0000]Error 2[/COLOR]
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'
Makefile:1893: [COLOR=#ff0000]recipe for target 'modules' failed[/COLOR]
[COLOR=#ff0000]make: *** [modules] Error 2[/COLOR]

---

### Post by chili555 on 2018-10-29
In a virtual machine running 4.15.0-29, it makes for me without error, albeit a few warnings.

Please tell us the result of the following:```
sudo dpkg -s build-essential | grep Status
sudo dpkg -s libelf-dev | grep Status
```You are indeed working on the git I referenced above, correct? [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

---

### Post by n2te on 2018-10-29
The make command returns errors.
The sudo make install teturns errors and says failed.
sudo make install
[sudo] password for ed: 
install -p -m 644 8821cu.ko  /lib/modules/4.15.0-38-generic/kernel/drivers/net/wireless/
install: cannot stat '8821cu.ko': No such file or directory
[COLOR=#ff0000]Makefile:1899: recipe for target 'install' failed[/COLOR]
make: *** [install] Error 1

Now what? What did I do wrong?

---

### Post by chili555 on 2018-10-29
> Now what? What did I do wrong?Please see my questions just above.

---

### Post by n2te on 2018-10-29
Sorry. My mistake. Overlooked:

~$ sudo dpkg -s build-essential | grep Status
**[COLOR=#006400]Status: install ok installed[/COLOR]**
~$ sudo dpkg -s libelf-dev | grep Status
**[COLOR=#006400]Status: install ok installed[/COLOR]**

---

### Post by chili555 on 2018-10-29
> You are indeed working on the git I referenced above, correct? [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)
Correct? Or some other??

---

### Post by n2te on 2018-10-29
sudo make install
install -p -m 644 8821cu.ko  /lib/modules/4.15.0-38-generic/kernel/drivers/net/wireless/
install: cannot stat '8821cu.ko': [COLOR=#ff0000]No such file or directory[/COLOR]
Makefile:1899: [COLOR=#ff0000]recipe for target 'install' failed[/COLOR]
make: *** [install] Error 1
sudo modprobe 8821CU
modprobe: [COLOR=#ff0000]FATAL: Module 8821CU not found in directory /lib/modules/4.15.0-38-generic

[/COLOR][COLOR=#000000][/COLOR]

---

### Post by chili555 on 2018-10-29
It will do you no good to run the commands over and over and expect a different result.

Again, you are indeed working on the git I referenced above, correct? [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

Is that correct? Or some other git??

Do NOT run the commands again. Nothing will change until we change something else.

---

### Post by n2te on 2018-10-29
Sorry. Yes, I downloaded the zip file from [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU) and then extracted the contents to ~/Downloads/rtl8821CU
Then changed to the sub folder with all the files. It's cranking away now. ......

OK. All commands ran with no errors. excellent.
Now doing a reboot and looking to see if the USB dongle is recognized. Will report back in a moment....

---

### Post by n2te on 2018-10-29
IT WORKED! USB WiFi dongle is now recognized and WiFi connectivity has been achieved.  I did verify that the device does not work if I boot v4.19. However when I switch back to 4.15 it does works fine. 
So therefore in the future is there any reason for me to update the kernel to a higher level version since obviously that would cause my USB WiFi dongle to cease working?
Though this exercise was a bit frustrating, the process was MOST enjoyable and my thanks to you for your assistance.

---

### Post by chili555 on 2018-10-30
> So therefore in the future is there any reason for me to update the kernel to a higher level version since obviously that would cause my USB WiFi dongle to cease working?The driver is not going to work in kernel version 4.19; you've shown that it won't compile. Unless you need 4.19 for some other purpose, I'd remove it altogether. If you need guidance on how to do so safely, please post back.

There is always a reson to upgrade to the next higher kernel version, namely security and bug fixes. However, after the update and after the requested reboot, simply re-compile against the newer kernel version:

```
cd  ~/Downloads/rtl8821CU
make clean
make
sudo make install
sudo modprobe 8821cu
```Please retain the file and these instructions for that time.

---

### Post by n2te on 2018-12-27
All has been working fine. Occasionally however the system (Ubuntu 18.04) will stop recognizing the wifi device and I will have to go thru the same steps as before to reinstall it. 

cd ~/Downloads/rtl8821CU
make clean
make
sudo make install
sudo modprobe 8821CU

Now I need to do the re-install again today but the same process encounters an error when executing the last step: modprobe 8821CU. The error is:
modprobe: FATAL: Module 8821CU not found in directory /lib/modules/4.15.0-43-generic

Can someone tell me what the reason might be that I'm getting this error and what fix I might employ?

---

### Post by chili555 on 2018-12-27
What is the exact result of the ‘make’ step, please?

---

### Post by n2te on 2018-12-27
Interesting. It works now. I moved the PC in question back into my 'computer' room and connected it directly to my home network and upon boot up the machine recognized my wifi dongle and connected to my home wifi-lan. After powering down the PC I returned it to the family TV room and subsequent to boot up it recognized the wifi dongle once again and connected to my home wifi lan. Can I conclude that having a wired lan connection at boot-up took care of some missing dependency of some sort during the boot and sys setup process? But it works now. Strange.

---

### Post by chili555 on 2018-12-27
> Can I conclude that having a wired lan connection at boot-up took care of some missing dependency of some sort during the boot and sys setup process? It's very hard to determine without a thorough examination of the logs.

Let's not fix what isn't broken.

Enjoy!

---

