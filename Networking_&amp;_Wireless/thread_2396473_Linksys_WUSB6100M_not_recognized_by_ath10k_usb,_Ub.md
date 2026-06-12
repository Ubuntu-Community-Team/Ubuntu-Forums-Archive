---
title: "Linksys WUSB6100M not recognized by ath10k_usb, Ubuntu 18.04"
date: 2018-07-16
forum: Networking &amp; Wireless
---

### Post by violagirl23 on 2018-07-16
I am dual booting Windows 10 and Ubuntu 18.04. My USB WiFi adapter, WUSB6100M, is not recognized by Ubuntu. The adapter works properly on Windows.

I followed the instructions listed here to prepare the **ath10k_usb** module:
[github.com/erstrom/linux-ath/wiki/Firmware]("https://github.com/erstrom/linux-ath/wiki/Firmware")

I created my **firmware-usb-5.bin** and **board-usb.bin** files with the Linksys Windows 10 drivers:
[downloads.linksys.com/downloads/driver/WUSB6100M_Win10v11.1.0.268-275.zip]("http://downloads.linksys.com/downloads/driver/WUSB6100M_Win10v11.1.0.268-275.zip")

I also copied **board.bin** and **board-2.bin** to **/lib/firmware/ath10k/QCA9377/hw1.0** from the below github repo, in case they are needed.
[github.com/erstrom/ath10k-firmware/tree/master/QCA9377/hw1.0]("https://github.com/erstrom/ath10k-firmware/tree/master/QCA9377/hw1.0")

The final directory looks like so:
```
mayka@Work:/lib/firmware/ath10k/QCA9377/hw1.0$ ls -lia
total 984
131096 drwxr-xr-x 2 root root   4096 Jul 15 19:46 .
131089 drwxr-xr-x 3 root root   4096 Jul 15 19:03 ..
131079 -rwxr-xr-x 1 root root 304308 Jul 15 18:58 board-2.bin
131275 -rwxr-xr-x 1 root root   8124 Jul 15 18:58 board.bin
131155 lrwxrwxrwx 1 root root     38 Jul 15 18:28 board-usb.bin -> eeprom_qca9377_7_1p1_Robin_clpc_ce.bin
131270 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_as.bin
131271 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_ce.bin
131272 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_fcc.bin
131273 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_ic.bin
131274 -rwxr-xr-x 1 root root 600376 Jul 15 18:26 firmware-usb-5.bin
131276 -rw-r--r-- 1 root root  46143 Jul 15 19:46 notice_ath10k_firmware-5.txt
```

When I reboot, my adapter isn't recognized. Here is the wireless-info output: [wireless-info.txt]("https://pastebin.com/raw/CmUqrbe2")

The router is too far away to feasibly use a wired connection, so I mirrored the entire **bionic** repository on another machine with apt-mirror.

This enabled me to run **sudo apt update** and **sudo apt dist-upgrade**, then I installed **build-essential** and **git** on my local machine with this mirror repository and proceeded to try to install backports-4.4.2-1, but it fails on **make**, as below. Not sure what else to try at this point. I'm honestly a bit stumped.

```
mayka@Work:~/Desktop/backports-4.4.2-1$ sudo make defconfig-ath10k
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#

mayka@Work:~/Desktop/backports-4.4.2-1$ sudo make
make[5]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/mayka/Desktop/backports-4.4.2-1/compat/main.o
  LD [M]  /home/mayka/Desktop/backports-4.4.2-1/compat/compat.o
  CC [M]  /home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/main.o
  CC [M]  /home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.o
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c: In function &#8216;dynamic_country_user_possible&#8217;:
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c:119:6: error: implicit declaration of function &#8216;config_enabled&#8217;; did you mean &#8216;x2apic_enabled&#8217;? [-Werror=implicit-function-declaration]
  if (config_enabled(CPTCFG_ATH_REG_DYNAMIC_USER_CERT_TESTING))
      ^~~~~~~~~~~~~~
      x2apic_enabled
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c:119:21: error: &#8216;CPTCFG_ATH_REG_DYNAMIC_USER_CERT_TESTING&#8217; undeclared (first use in this function)
  if (config_enabled(CPTCFG_ATH_REG_DYNAMIC_USER_CERT_TESTING))
                     ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c:119:21: note: each undeclared identifier is reported only once for each function it appears in
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c: In function &#8216;ath_reg_dyn_country_user_allow&#8217;:
/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.c:191:22: error: &#8216;CPTCFG_ATH_REG_DYNAMIC_USER_REG_HINTS&#8217; undeclared (first use in this function)
  if (!config_enabled(CPTCFG_ATH_REG_DYNAMIC_USER_REG_HINTS))
                      ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.o' failed
make[7]: *** [/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath/regd.o] Error 1
scripts/Makefile.build:606: recipe for target '/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath' failed
make[6]: *** [/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless/ath] Error 2
scripts/Makefile.build:606: recipe for target '/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless' failed
make[5]: *** [/home/mayka/Desktop/backports-4.4.2-1/drivers/net/wireless] Error 2
Makefile:1552: recipe for target '_module_/home/mayka/Desktop/backports-4.4.2-1' failed
make[4]: *** [_module_/home/mayka/Desktop/backports-4.4.2-1] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[3]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
```

---

### Post by chili555 on 2018-07-16
First, it is fruitless to try to build a new driver from the corresponding 4.4 kernel (backports-4.4.2-1) and install it in your shiny, new 4.15 kernel. Furthermore, the issue seems to be firmware. From your paste:> usb 1-4: failed to fetch board data for bus=usb,vendor=13b1,device=0042,subsystem-vendor=0000,subsystem-device=0000 from ath10k/QCA9377/hw1.0/board-2.binYour firmware file looks like:> mayka@Work:/lib/firmware/ath10k/QCA9377/hw1.0$ ls -lia
total 984
131096 drwxr-xr-x 2 root root   4096 Jul 15 19:46 .
131089 drwxr-xr-x 3 root root   4096 Jul 15 19:03 ..
131079 -rwxr-xr-x 1 root root [COLOR="#FF0000"]304308[/COLOR] Jul 15 18:58 board-2.bin
131275 -rwxr-xr-x 1 root root   8124 Jul 15 18:58 board.bin
131155 lrwxrwxrwx 1 root root     38 Jul 15 18:28 board-usb.bin -> eeprom_qca9377_7_1p1_Robin_clpc_ce.bin
131270 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_as.bin
131271 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_ce.bin
131272 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_fcc.bin
131273 -rwxr-xr-x 1 root root   8124 Jul 15 18:26 eeprom_qca9377_7_1p1_Robin_clpc_ic.bin
131274 -rwxr-xr-x 1 root root 600376 Jul 15 18:26 firmware-usb-5.bin
131276 -rw-r--r-- 1 root root  46143 Jul 15 19:46 notice_ath10k_firmware-5.txtHowever, when I clone the firmware git you quoted, I get:```

chili@T440p:~/Desktop/Forum/erstrom/ath10k-firmware/QCA9377/hw1.0$ ls -al
total 1080
drwxr-xr-x 3 chili chili   4096 Jul 16 10:10 .
drwxr-xr-x 3 chili chili   4096 Jul 16 10:10 ..
-rw-r--r-- 1 chili chili [COLOR="#FF0000"]427668[/COLOR] Jul 16 10:10 board-2.bin
-rw-r--r-- 1 chili chili   8124 Jul 16 10:10 board.bin
-rw-r--r-- 1 chili chili 605908 Jul 16 10:10 firmware-5.bin_WLAN.TF.1.0-00267-1
-rw-r--r-- 1 chili chili  46142 Jul 16 10:10 notice.txt_WLAN.TF.1.0-00267-1
drwxr-xr-x 2 chili chili   4096 Jul 16 10:10 untested

```Please retrace your steps, reboot and let us see:```
dmesg | grep ath
```

---

### Post by violagirl23 on 2018-07-18
> **chili555 said:**
> Please retrace your steps, reboot and let us see:```
dmesg | grep ath
```

 I backed up everything and created a new empty **QCA9377** folder, and then I retraced my steps. Here is the new output of ls -al.

```
ls -al /lib/firmware/ath10k/QCA9377/hw1.0/
total 1696
drwxr-xr-x 2 root  root    4096 Jul 17 20:02 .
drwxr-xr-x 3 root  root    4096 Jul 17 19:52 ..
-rw-r--r-- 1 root  root  427668 Jul 17 20:02 board-2.bin
-rw-r--r-- 1 root  root    8124 Jul 17 20:02 board.bin
lrwxrwxrwx 1 root  root      39 Jul 17 19:53 board-usb.bin -> eeprom_qca9377_7_1p1_Robin_clpc_fcc.bin
-rw-rw-r-- 1 mayka mayka   8124 Jul 17 19:47 eeprom_qca9377_7_1p1_Robin_clpc_as.bin
-rw-rw-r-- 1 mayka mayka   8124 Jul 17 19:47 eeprom_qca9377_7_1p1_Robin_clpc_ce.bin
-rw-rw-r-- 1 mayka mayka   8124 Jul 17 19:47 eeprom_qca9377_7_1p1_Robin_clpc_fcc.bin
-rw-rw-r-- 1 mayka mayka   8124 Jul 17 19:47 eeprom_qca9377_7_1p1_Robin_clpc_ic.bin
-rw-r--r-- 1 root  root  605908 Jul 17 20:02 firmware-5.bin_WLAN.TF.1.0-00267-1
-rw-rw-r-- 1 mayka mayka 600376 Jul 17 19:49 firmware-usb-5.bin
-rw-r--r-- 1 root  root   46142 Jul 17 20:02 notice.txt_WLAN.TF.1.0-00267-1
```

I copied everything in that folder from the firmware git mentioned in the original post, except for **firmware-usb-5.bin**, which I generated with the ath10k-fwencoder script, as well as the **eeprom*** files, which are from the x64 folder inside **WUSB6100M_Win10/**. (This **x64** folder is also where I extracted **otp_AR6320.bin** and **athwlan_AR6320.bin** from, to use as the source files I fed to the ath10k-fwencoder script.)

Here is the output of dmesg:

```
dmesg | grep ath
[   20.665780] usb 1-4: WARNING: ath10k USB support is incomplete, don't expect anything to work!
[   20.665826] usbcore: registered new interface driver ath10k_usb
[   20.666543] usb 1-4: Direct firmware load for ath10k/pre-cal-usb-1-4.bin failed with error -2
[   20.666552] usb 1-4: Direct firmware load for ath10k/cal-usb-1-4.bin failed with error -2
[   20.696036] usb 1-4: Direct firmware load for ath10k/QCA9377/hw1.0/firmware-usb-6.bin failed with error -2
[   20.754376] usb 1-4: failed to fetch board data for bus=usb,vendor=13b1,device=0042,subsystem-vendor=0000,subsystem-device=0000 from ath10k/QCA9377/hw1.0/board-2.bin
```

---

### Post by chili555 on 2018-07-18
I have been Googling this subject for quite some time and I find many mentions of  ath10k_usb and many issues but, so far, not much success. I am cautious when I read this in your log:> usb 1-4: WARNING: ath10k USB support is incomplete, don't expect anything to work!Let's see if there are further clues here:```
dmesg | grep usb
```

---

