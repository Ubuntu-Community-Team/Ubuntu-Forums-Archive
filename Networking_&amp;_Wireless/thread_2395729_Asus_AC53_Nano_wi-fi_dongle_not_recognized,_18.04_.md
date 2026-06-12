---
title: "Asus AC53 Nano wi-fi dongle not recognized, 18.04 LTS"
date: 2018-07-05
forum: Networking &amp; Wireless
---

### Post by badge22 on 2018-07-05
Hello, 
After a fresh install of 18.04 LTS my USB wi-fi dongle no longer works. When using 16.04 LTS I was able to use the rtl8822bu driver, but it doesn't seem to work with the new install. 
I get the following error messages when I try the make command in my rtl8822bu-master folder.

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-23-generic/build M=/home/badge/Desktop/rtl8822bu-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-23-generic'
arch/x86/Makefile:156: CONFIG_X86_X32 enabled but no binutils support
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/badge/Desktop/rtl8822bu-master/core/rtw_cmd.o
/bin/sh: 1: gcc: not found
scripts/Makefile.build:332: recipe for target '/home/badge/Desktop/rtl8822bu-master/core/rtw_cmd.o' failed
make[2]: *** [/home/badge/Desktop/rtl8822bu-master/core/rtw_cmd.o] Error 127
Makefile:1552: recipe for target '_module_/home/badge/Desktop/rtl8822bu-master' failed
make[1]: *** [_module_/home/badge/Desktop/rtl8822bu-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2

```

I ran the wireless script and the results are here
[http://paste.ubuntu.com/p/4sfFRf2XJx/](http://paste.ubuntu.com/p/4sfFRf2XJx/)

Also, I have this PC  set up as dual boot now if this makes any difference

Thank you,
Chris

---

### Post by praseodym on 2018-07-06
[https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_26334.20180126_COEX20171012-5044](https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_26334.20180126_COEX20171012-5044)

Is it this one (updated!)?

---

### Post by badge22 on 2018-07-10
I had not tried that version yet. Unfortunately it isn't working either. I didn't get any errors during the make or make install step, but after a reboot the wifi dongle still isn't showing up. 

I ran the wireless script again after reboot.
[https://pastebin.com/8EU7r151](https://pastebin.com/8EU7r151)

---

### Post by chili555 on 2018-07-10
That driver doesn't cover your 184C device, but this one does: [https://github.com/jeremyb31/rtl8822bu](https://github.com/jeremyb31/rtl8822bu)

Please try again. If you need a step-by-step, please post back and we'll be happy to help.

---

### Post by badge22 on 2018-07-10
Unfortunately I got this error on the make step using the driver from jeremyb31.

```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-23-generic/build M=/home/badge/rtl8822bu-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-23-generic'
  CC [M]  /home/badge/rtl8822bu-master/core/rtw_cmd.o
In file included from /home/badge/rtl8822bu-master/include/osdep_service.h:41:0,
                 from /home/badge/rtl8822bu-master/include/drv_types.h:32,
                 from /home/badge/rtl8822bu-master/core/rtw_cmd.c:22:
/home/badge/rtl8822bu-master/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/badge/rtl8822bu-master/include/osdep_service_linux.h:262:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/badge/rtl8822bu-master/include/osdep_service_linux.h:263:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/badge/rtl8822bu-master/core/rtw_cmd.o' failed
make[2]: *** [/home/badge/rtl8822bu-master/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/home/badge/rtl8822bu-master' failed
make[1]: *** [_module_/home/badge/rtl8822bu-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2
```

The steps I have been following are download zip, extract, open terminal in extracted folder then run the following commands

```
sudo make

sudo make install

sudo reboot

```

I have tried using make clean as well before running these steps, but no luck yet.
Thank you for your help.

---

### Post by chili555 on 2018-07-11
Please try this:```
cd ~
git clone https://github.com/FomalhautWeisszwerg/rtl8822bu.git
cd rtl8822bu
nano os_dep/linux/usb_intf.c
```Change this section at about line 222, from this:```
#ifdef CONFIG_RTL8822B
	/*=== Realtek demoboard ===*/
	{USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
	{USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
	{USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
	{USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
	{USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```To this:```
#ifdef CONFIG_RTL8822B
        /*=== Realtek demoboard ===*/
        {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
        {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
        {USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
        {USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
       [COLOR="#FF0000"] {USB_DEVICE(0x0B05, 0x184C), .driver_info = RTL8822B}, /* ASUS USB AC53 */[/COLOR]
        {USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
        {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```I have highlighted the line you will add.

Spacing, indentation, etc. are crucial and must be perfect. Proofread carefully twice. Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor. 

Now back to the terminal:```
make
sudo make install
sudo modprobe 8822bu
```Any improvement?

---

### Post by badge22 on 2018-07-11
Success! I followed your steps and rebooted. 

The Asus AC53 wifi dongle was recognized and has worked flawlessly for an hour so far on 18.04 LTS.

Thank you so much!

---

### Post by chili555 on 2018-07-11
> **badge22 said:**
> Success! I followed your steps and rebooted. 

The Asus AC53 wifi dongle was recognized and has worked flawlessly for an hour so far on 18.04 LTS.

Thank you so much!Awesome! Glad it's working!

After a kernel update, recompile:```
cd ~/rtl8822bu
make clean
make
sudo make install
sudo modprobe 8822bu
```Have fun!

---

### Post by crackity2 on 2018-08-23
> **chili555 said:**
> Please try this:```
cd ~
git clone https://github.com/FomalhautWeisszwerg/rtl8822bu.git
cd rtl8822bu
nano os_dep/linux/usb_intf.c
```Change this section at about line 222, from this:```
#ifdef CONFIG_RTL8822B
    /*=== Realtek demoboard ===*/
    {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
    {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
    {USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
    {USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
    {USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
    {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```To this:```
#ifdef CONFIG_RTL8822B
        /*=== Realtek demoboard ===*/
        {USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
        {USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
        {USB_DEVICE(0x7392, 0xC822), .driver_info = RTL8822B}, /* Edimax - EW-7822UTC */
        {USB_DEVICE(0x13B1, 0x0043), .driver_info = RTL8822B}, /* Linksys - WUSB6400M */
       [COLOR=#FF0000] {USB_DEVICE(0x0B05, 0x184C), .driver_info = RTL8822B}, /* ASUS USB AC53 */[/COLOR]
        {USB_DEVICE(0x0BDA, 0xB812), .driver_info = RTL8822B},
        {USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```I have highlighted the line you will add.

Spacing, indentation, etc. are crucial and must be perfect. Proofread carefully twice. Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor. 

Now back to the terminal:```
make
sudo make install
sudo modprobe 8822bu
```Any improvement?


Thanks so much, this solution worked for me as well!

---

### Post by ishchuchkin on 2018-09-09
Hi [COLOR=#DD4814]chili555[/COLOR], doing as you said, but every time i'm getting this
ian@ian-23-k300xt:~/rtl8822bu$ sudo make install
[sudo] password for ian: 
install -p -m 644 8822bu.ko  /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.15.0-33-generic
ian@ian-23-k300xt:~/rtl8822bu$ sudo modprobe 8822bu
modprobe: ERROR: could not insert '8822bu': Required key not available

Ubuntu 18.04

Any ideas?
Thanks

---

### Post by chili555 on 2018-09-09
> **ishchuchkin said:**
> Hi [COLOR=#DD4814]chili555[/COLOR], doing as you said, but every time i'm getting this
ian@ian-23-k300xt:~/rtl8822bu$ sudo make install
[sudo] password for ian: 
install -p -m 644 8822bu.ko  /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.15.0-33-generic
ian@ian-23-k300xt:~/rtl8822bu$ sudo modprobe 8822bu
modprobe: ERROR: could not insert '8822bu': [COLOR="#FF0000"]Required key not available[/COLOR]

Ubuntu 18.04

Any ideas?
ThanksPlease check here: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by joeydag on 2019-03-11
Hi, I'm a newbie and I'm in trouble with this dongle. 

I did all your steps but when I put "make", I see this error:

```
make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-46-generic/build M=/home/joey/rtl8822bu modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.15.0-46-generic'
arch/x86/Makefile:156: CONFIG_X86_X32 enabled but no binutils support
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/joey/rtl8822bu/core/rtw_cmd.o
/bin/sh: 1: gcc: not found
scripts/Makefile.build:332: recipe for target '/home/joey/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/joey/rtl8822bu/core/rtw_cmd.o] Error 127
Makefile:1551: recipe for target '_module_/home/joey/rtl8822bu' failed
make[1]: *** [_module_/home/joey/rtl8822bu] Error 2
make[1]: se sale del directorio '/usr/src/linux-headers-4.15.0-46-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2

```

what could it happen?

---

### Post by jeremy31 on 2019-03-11
> **joeydag said:**
> Hi, I'm a newbie and I'm in trouble with this dongle. 

I did all your steps but when I put "make", I see this error:

```
make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-46-generic/build M=/home/joey/rtl8822bu modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.15.0-46-generic'
arch/x86/Makefile:156: CONFIG_X86_X32 enabled but no binutils support
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/joey/rtl8822bu/core/rtw_cmd.o
/bin/sh: 1: gcc: not found
scripts/Makefile.build:332: recipe for target '/home/joey/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/joey/rtl8822bu/core/rtw_cmd.o] Error 127
Makefile:1551: recipe for target '_module_/home/joey/rtl8822bu' failed
make[1]: *** [_module_/home/joey/rtl8822bu] Error 2
make[1]: se sale del directorio '/usr/src/linux-headers-4.15.0-46-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2

```

what could it happen?
Did you happen to do ```
sudo apt install build-essential
```

---

### Post by joeydag on 2019-03-11
Thanks, this step works! I will study about this. 

But then, in modprobe, I get this error:

 sudo modprobe 8822bu
modprobe: FATAL: Module 8822bu not found in directory /lib/modules/4.15.0-46-generic



Any idea?

---

### Post by jeremy31 on 2019-03-11
You may just need to reboot

---

### Post by joeydag on 2019-03-11
I'm sorry, I forget the line: 
sudo make install

Anyway, I will reboot and try the Dongle. Many thanks.

Edit: Rebooted and all working fine, thanks for all!

---

### Post by skegness1961 on 2019-10-29
These instructions worked perfectly for me. My sincere thanks to you for your accurate and clear advice.

---

### Post by skegness1961 on 2019-10-29
Perfect solution - Thank you very much.

---

### Post by szydas on 2020-08-01
I'm complete noob in programming. I did everything like described and my module won't compile. It stops on error on line 2087 "set_fs(get_ds());|           ^~~~~~~~|           ||           int" and closes with "error: incompatible type for argument 1 of ‘set_fs’ " message. How can i fix it?

---

### Post by chili555 on 2020-08-01
> **szydas said:**
> I'm complete noob in programming. I did everything like described and my module won't compile. It stops on error on line 2087 "set_fs(get_ds());|           ^~~~~~~~|           ||           int" and closes with "error: incompatible type for argument 1 of ‘set_fs’ " message. How can i fix it?
The solution that I posted is now a bit old and stale.

Please start your own new question and I'll be happy to assist.

Please be sure to include the result of:

```
lsusb
uname -r
```

---

### Post by coffeecat on 2020-08-02
Old, and repeatedly necromanced, thread closed.

@szydas, please start your own thread with the information that chili555 requests.

To anyone else needing help: **please start your own thread**.

---

