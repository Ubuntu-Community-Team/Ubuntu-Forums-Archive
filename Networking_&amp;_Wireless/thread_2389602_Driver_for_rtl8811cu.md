---
title: "Driver for rtl8811cu?"
date: 2018-04-19
forum: Networking &amp; Wireless
---

### Post by ariel8 on 2018-04-19
is there a driver available for the realtek rtl8811cu? i've been looking everywhere and culd not find one for the life of me, the one for 8811au doesnt seem to want to work :(

---

### Post by chili555 on 2018-04-19
How about if we start at the beginning. Please run and post:```
lsusb
uname -r
```

---

### Post by ariel8 on 2018-04-19
```

   ariel@ariel-lin:~$ lsusbBus 002 Device 002: ID 0bda:0316 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04f2:b5ab Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 04f2:b5ac Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:c811 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 03f0:094a Hewlett-Packard Optical Mouse [672662-001]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ariel@ariel-lin:~$ uname -r
4.13.0-38-generic

```
0bda:c811 is the usb dongle

---

### Post by chili555 on 2018-04-19
> the one for 8811au doesnt seem to want to workWhich one, exactly? In what way did it not work? Did it compile or not? Did it load and drive your device or not? Did it connect? Drop? Or...what??

---

### Post by ariel8 on 2018-04-19
[https://github.com/sloretz/rtl8811au](https://github.com/sloretz/rtl8811au)
didnt compile, but i solved those issues, it did load but the device wasnt recognized

---

### Post by chili555 on 2018-04-20
Regrettably, I must admit that, after two days of searching, compiling, tweaking c code, etc., that I have no suggestions. In the git repository that you used, your c811 device isn't even mentioned. It is not surprising that it doesn't drive your device.

I wish I had better news.

```
#ifdef CONFIG_RTL8821A
        /*=== Realtek demoboard ===*/
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0811),.driver_info = RTL8821},/* Default ID */
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0821),.driver_info = RTL8821},/* Default ID */
	{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x8822),.driver_info = RTL8821},/* Default ID */
	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0x0820,0xff,0xff,0xff),.driver_info = RTL8821}, /* 8821AU */
	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0x0823,0xff,0xff,0xff),.driver_info = RTL8821}, /* 8821AU */
	/*=== Customer ID ===*/
	{USB_DEVICE(0x7392, 0xA811),.driver_info = RTL8821}, /* Edimax - Edimax */
	{USB_DEVICE(0x04BB, 0x0953),.driver_info = RTL8821}, /* I-O DATA - Edimax */
	{USB_DEVICE(0x2001, 0x3314),.driver_info = RTL8821}, /* D-Link - Cameo */
	{USB_DEVICE(0x2001, 0x3318),.driver_info = RTL8821}, /* D-Link - Cameo */
	{USB_DEVICE(0x0E66, 0x0023),.driver_info = RTL8821}, /* HAWKING - Edimax */
#endif
```Where is 0xC811? Would you like to try to add it and recompile?

---

### Post by ariel8 on 2018-04-20
added, installing, will let you know once i reboot

---

### Post by ariel8 on 2018-04-20
done, doesnt seem to work :/

---

### Post by chili555 on 2018-04-21
After you added the device, did you make clean, make and sudo make install and then reboot? Does the device appear in modinfo?

---

### Post by ariel8 on 2018-04-21
yes, i did, it doesnt seem to appear in modinfo, the Makefile config is set to rtl8821A, the closest is rtl8821ae which is a PCI driver..?

---

### Post by chili555 on 2018-04-21
Please paste your usb_intf.c after you modified it: [http://paste.ubuntu.com](http://paste.ubuntu.com) and give me the link.

---

### Post by ariel8 on 2018-04-21
wait! IT APPEARS TO BE WORKING

---

### Post by ariel8 on 2018-04-21
never mind, the device is detected, but it does not pick up any signals

---

### Post by ariel8 on 2018-04-21
[https://paste.ubuntu.com/p/gNZygj856X/](https://paste.ubuntu.com/p/gNZygj856X/)

---

### Post by chili555 on 2018-04-21
> **ariel8 said:**
> never mind, the device is detected, but it does not pick up any signalsAny clues in the log?```
rfkill list all
dmesg | grep 881
dmesg | grep -i rtl
```

---

### Post by ariel8 on 2018-04-21
[https://paste.ubuntu.com/p/YJ6cMgDNPT/](https://paste.ubuntu.com/p/YJ6cMgDNPT/)

---

### Post by chili555 on 2018-04-21
> rtl8812au_hal_init: Download FirmwareDoes modinfo say anything about firmware?

Is an interface created?```
iwconfig
```Does it scan?```
nmcli dev wifi list
```

---

### Post by ariel8 on 2018-04-21
```
enx00e04c1c4abb  unassociated  Nickname:"<WIFI@REALTEK>"          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```
doesnt scan

---

### Post by ariel8 on 2018-05-03
anyone have any ideas?

---

### Post by waynewu411 on 2018-05-28
Hi guys,

I'm just struggling on a USB WIFI dongle with the same device id 0xC811 from realtek on raspberry pi with tinycore linux.
After searching for a longtime on google, I found this project on Github: [https://github.com/zebulon2/rtl8812au-driver-5.2.20](https://github.com/zebulon2/rtl8812au-driver-5.2.20) which include the support for this device id. But it seems that the driver needs some modification to support raspberry pi platform and it's out of my capability to do that. Hope someone can give it a fix.

---

### Post by chili555 on 2018-05-28
> **waynewu411 said:**
> Hi guys,

I'm just struggling on a USB WIFI dongle with the same device id 0xC811 from realtek on raspberry pi with tinycore linux.
After searching for a longtime on google, I found this project on Github: [https://github.com/zebulon2/rtl8812au-driver-5.2.20](https://github.com/zebulon2/rtl8812au-driver-5.2.20) which include the support for this device id. But it seems that the driver needs some modification to support raspberry pi platform and it's out of my capability to do that. Hope someone can give it a fix.I have attempted some of the changes apparent to me, a curious tinkerer, not a developer. I can't get it to 'make' at all.

I suggest that you address your request to the  holder of the github repository, zebulon2.

---

### Post by zimmercy on 2018-05-30
Please try [https://github.com/MingxuZhang/rtl8821cu](https://github.com/MingxuZhang/rtl8821cu) which helped me for driving my rtl8811cu device.
Hope this can help you.

---

### Post by chili555 on 2018-05-30
> **zimmercy said:**
> Please try [https://github.com/MingxuZhang/rtl8821cu](https://github.com/MingxuZhang/rtl8821cu) which helped me for driving my rtl8811cu device.
Hope this can help you.It won't compile for me on my 4.15.0-xx kernel. Those of you with earlier kernels may have better luck.

Post back if you'd like a step-by-step.

> /home/chili/Desktop/Forum/MingxuZhang/rtl8821cu/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/chili/Desktop/Forum/MingxuZhang/rtl8821cu/include/osdep_service_linux.h:302:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/chili/Desktop/Forum/MingxuZhang/rtl8821cu/include/osdep_service_linux.h:303:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/chili/Desktop/Forum/MingxuZhang/rtl8821cu/core/rtw_cmd.o' failed


---

### Post by whitebatman on 2018-05-30
You could try my version of driver [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU). It builds and works on my ubuntu 18.04 with 4.15.0 kernel.

---

### Post by whitebatman on 2018-05-30
My driver works fine on ubuntu, but when I try to compile it on Raspberry Pi I still get this error:

> make ARCH=arm CROSS_COMPILE= -C /lib/modules/4.14.34+/build M=/home/pi/rtl8821CU  modulesmake[1]: Entering directory '/usr/src/linux-headers-4.14.34+'
  CC [M]  /home/pi/rtl8821CU/core/rtw_cmd.o
gcc: error: -mfloat-abi=soft and -mfloat-abi=hard may not be used together
scripts/Makefile.build:328: recipe for target '/home/pi/rtl8821CU/core/rtw_cmd.o' failed
make[2]: *** [/home/pi/rtl8821CU/core/rtw_cmd.o] Error 1
Makefile:1528: recipe for target '_module_/home/pi/rtl8821CU' failed
make[1]: *** [_module_/home/pi/rtl8821CU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.14.34+'
Makefile:1906: recipe for target 'modules' failed
make: *** [modules] Error 2


Why is there -mfloat-abi=soft gcc option even though it isn't set in Makefile?

---

### Post by whitebatman on 2018-05-31
I've managed to build the driver by modifying Makefile in kernel headers. It isn't the best possible solution, but it works. You can find my workaround in readme of my repo.
[https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

---

### Post by whitebatman on 2018-06-04
I fixed the driver to build on Raspberry Pi. Unfortunately there isn't any driver that supports 80 MHz channel width.

---

### Post by icefir on 2018-06-07
Wow its working for me :D Thx!
Under Manjaro Linux (Arch) x86 with kernel 4.14

Just to add a few notes here in case:

I'm using TP-Link TL-WDN5200 600M usb dongle, driverless version, for which in western it was named TP-Link T2U
So, as I've checked through online data, it seems they *were* using mt7610u, thus I went ahead and tried that driver
apparently not working.
After hours of messing around, finally realized that I need to use usb_modeswitch to set it to wifi mode (credit to here: [http://forum.ubuntu.org.cn/viewtopic.php?p=3193649](http://forum.ubuntu.org.cn/viewtopic.php?p=3193649))
Also, turns out unmount the usb storage also works.
Initial USB storage ID: 0bda:1a2b Realtek Semiconductor Corp.
Mode switch: ```
sudo usb_modeswitch -KW -v 0bda -p 1a2b
```
Or simply umount usb storage device.
Afterward ID: 0bda:c811 Realtek Semiconductor Corp
Yep. You guessed it. They've changed the chipset without saying anything :P

Well rest is easy, went ahead and compiled your version of the driver, Bingo everything is working like a charm :D

---

### Post by holiday on 2018-07-26
> **whitebatman said:**
> I've managed to build the driver by modifying Makefile in kernel headers. It isn't the best possible solution, but it works. You can find my workaround in readme of my repo.
[https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

From your repo -- Builds, installs, works for me on 18.04 using wpa_supplicant driver nl80211

Thank you.

---

### Post by tpkellis54 on 2018-10-13
Hi whitebatman

I have bought a wifi dongle with 5ghz so i can get fast wifi from vigin media 106 mbps.  It has a driver file for rtl881cu (also called confusingly rtl8821cu) and another for rtl8812bu. All very confusing to me as i dont really understand what means what. Will your driver work? How to i  get it to install? Do i have to take out existing slow pci e wireless card? How do i install your github driver? what  dkms? getting confused now!!!

---

### Post by tpkellis54 on 2018-10-13
Hi All

Whitebatman rtl8811cu driver works for me.  Wow. So i now have blazingly fast wifi 100 plus mbps on 5ghz 882.11ac wifi usb donle. Amazing.
i just followed Whitebatman instructions (had to find out how to clone github but its easy) and it worked. Wonderful.

Guess the driver thingy for rtl881cu is solved now!!!!

---

### Post by lkh1966 on 2018-12-20
Thks to Whitebatman's driver (RTL8821CU), it works for my RTL8811CU (yes, the chipset no. don't tally but it works). For my case, I have to do this in Terminal:
[COLOR=#242729][FONT=Arial]sudo apt-get install linux-headers-generic build-essential git
sudo make
sudo make install

I didn't try with DKMS. FYI, my USB dongle is a generic no brand 600mbps dual band AC adapter (bought cheap from eBay). Got it for my HTPC (an old Dell Optiplex Core2Duo desktop).[/FONT][/COLOR]

---

### Post by sergiojaj on 2019-02-03
> **whitebatman said:**
> I've managed to build the driver by modifying Makefile in kernel headers. It isn't the best possible solution, but it works. You can find my workaround in readme of my repo.
[https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

Mate! Thanks you so much for all the work you've put on it! Just made my day happier :D

Cheers!

---

### Post by nguinto on 2019-04-28
Did not compile in 19.04

make output follows:
/home/neil/Downloads/rtl8821CU-5.2.5.3/rtl8821CU/os_dep/linux/ioctl_cfg80211.c: In function ‘rtw_get_systime_us’:
/home/neil/Downloads/rtl8821CU-5.2.5.3/rtl8821CU/os_dep/linux/ioctl_cfg80211.c:339:2: error: implicit declaration of function ‘get_monotonic_boottime’; did you mean ‘getboottime’? [-Werror=implicit-function-declaration]
  get_monotonic_boottime(&ts);
  ^~~~~~~~~~~~~~~~~~~~~~
  getboottime
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:286: /home/neil/Downloads/rtl8821CU-5.2.5.3/rtl8821CU/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [Makefile:1584: _module_/home/neil/Downloads/rtl8821CU-5.2.5.3/rtl8821CU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.0.0-13-generic'
make: *** [Makefile:1923: modules] Error 2

---

### Post by Thole on 2019-05-04
Realtek RTL8811CU/RTL8821CU driver version 5.4.1 (latest version)

[https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU)

Tested and worked on Manjaro with Linux version 4.4 up to 5.1. But, I never tested it on Ubuntu.

---

### Post by intoanother on 2019-08-28
did anyone seem to get this working? 
I have a usb wifi adapter with rtl8811cu that i have tried everything i can find to get working and it just will not work on 18.04.
any help or sugestions ?

---

### Post by chili555 on 2019-08-28
> **intoanother said:**
> did anyone seem to get this working? 
I have a usb wifi adapter with rtl8811cu that i have tried everything i can find to get working and it just will not work on 18.04.
any help or sugestions ?Please start your own new question.

---

### Post by Frogs Hair on 2019-08-28
Outdated Info, Closed

---

