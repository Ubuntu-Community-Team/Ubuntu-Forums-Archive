---
title: "Problems installing Edimax or Aus wireless usb Ubuntu 16.04 LTS"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by franciscothekid on 2017-07-26
Hi 

I've tried installing two different usb wireless adapters without success.

The edimax comes with linux drivers but I'm unsure how to install them.

Have tried ndswrapper without success.

wireless info txt attached.

all suggestions appreciated.

Running

---

### Post by Bucky Ball on 2017-07-26
Welcome. Erm, did you run the wireless.info with one of the USB dongles plugged in? You should. There is nothing showing in your output.

Get rid of ndiswrapper. It will only make your job harder and is archaic and superceded in 99% of cases and may actually prevent your card from working. Forget about the Linux drivers that came with the dongles. They are generally useless.

Easiest at this point would be to plug in one of the dongles, open a terminal and run these two commands one after the other:

```
lsusb
sudo lshw -C network
```

Copy and save the output. Pull the first dongle out, plug in the other and run those commands again. Paste the output of those commands from both dongles here and we can see the wireless chipsets the two are using (hopefully) and proceed with the one that is going to be easiest to get up.

You don't have a wireless on/off physical button somewhere on the keyboard of you computer that is off do you? May be a silly question, but one never knows! I've done worse. :)

---

### Post by franciscothekid on 2017-07-26
Thanks for the quick response.

Edimax
```
testbench@testbench-GA-78LMT-USB3-6-0:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 7392:a611 Edimax Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:074b Microsoft Corp. 
Bus 003 Device 002: ID 1532:0032 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
testbench@testbench-GA-78LMT-USB3-6-0:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 1c:1b:0d:c6:a8:61
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.17 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:28 ioport:ce00(size=256) memory:fd9ff000-fd9fffff memory:fdffc000-fdffffff
testbench@testbench-GA-78LMT-USB3-6-0:~$ 
```

```
ASUS
testbench@testbench-GA-78LMT-USB3-6-0:~$: command not found
testbench@testbench-GA-78LMT-USB3-6-0:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0b05:184c ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:074b Microsoft Corp. 
Bus 003 Device 002: ID 1532:0032 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
testbench@testbench-GA-78LMT-USB3-6-0:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 1c:1b:0d:c6:a8:61
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.17 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:28 ioport:ce00(size=256) memory:fd9ff000-fd9fffff memory:fdffc000-fdffffff
```

---

### Post by Bucky Ball on 2017-07-26
Neither card is showing up. Do you, by any chance, have these plugged in to a USB hub? Try plugging directly into the computer and chuck us the output of the 'sudo lshw -C network' commands again.

Both show up in your 'lsusb' output, but your system is not picking them up beyond that for some reason.

Be aware that I am no expert but can provide some basic info and troubleshooting help. There are some 'wireless gurus' around here who will hopefully jump in sooner or later and may have a fix pronto. For now, let's see if we can get at least one of the cards recognised and maybe better. ;)

* Another command you can try to confirm it is not being seen (or is) is:

```
iwconfig
```

You are looking for signs of a 'Network Controller'. Something like this.

```
~$ iwconfig
wlp3s0    IEEE 802.11bgn  ESSID:"AccessPoint"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:0D:7F:DE:92:BA   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

enp2s0    no wireless extensions.

lo        no wireless extensions.

```

... but not exactly that. "AccessPoint" is the name of MY network. Yours should be the one you are connected to. "wlp3s0" is the wireless card, but yours may be called something different.

(PS: Please use [code] tags for terminal output. See green link in first line of my signature at bottom of post for how.)

---

### Post by franciscothekid on 2017-07-26
they are plugged directly into the mother board I/O panel.

---

### Post by Bucky Ball on 2017-07-26
Good. I have since edited my post. Please re-read. You were too quick for me. ;)

BTW, make sure you DO NOT have them both plugged in at the same time. One or the other, please.

---

### Post by chili555 on 2017-07-26
> Bus 001 Device 006: ID 0b05:184c ASUSTek Computer, Inc. That is your wireless device. Here is more information about it: [https://ubuntuforums.org/showthread.php?t=2362669](https://ubuntuforums.org/showthread.php?t=2362669) At post #11, our colleague Jeremy provides a working driver but only for 4.4 kernels. You are running 4.10.

This driver 'makes' for me with a few warnings but no errors and seems to cover your device:```
filename:       /home/chili/Desktop/Forum/rtl8822bu/8822bu.ko
version:        v5.1.0-5_17968.20160601_BTCOEX20160411-1400_beta
author:         Brandon Bailey <brandondanielbailey@gmail.com>
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5BD8B5BDDE5F15D44C8C01E
alias:          usb:v0BDApB82Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v[COLOR="#FF0000"]0B05[/COLOR]p[COLOR="#FF0000"]184C[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1812d*dc*dsc*dp*ic*isc*ip*in*
<snip>

```[https://github.com/brandon-bailey/rtl8822bu](https://github.com/brandon-bailey/rtl8822bu)

The process to build it is:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/brandon-bailey/rtl8822bu.git
cd rtl8822bu
make
sudo make install
sudo modprobe 8822bu
```

---

### Post by franciscothekid on 2017-07-26
no luck.
wireless connection still not showing.

---

### Post by chili555 on 2017-07-26
> **franciscothekid said:**
> no luck.
wireless connection still not showing.No luck means what?? You tried to compile it and there were errors? No errors but the driver doesn't modprobe? Or ... what?

Are there any clues in the log?```
sudo modprobe 8822bu && dmesg | grep 8822
iwconfig
```

---

### Post by franciscothekid on 2017-07-26
```
22
[sudo] password for testbench: 
[  205.972117] 8822bu: loading out-of-tree module taints kernel.
[  205.975115] 8822bu: module verification failed: signature and/or required key missing - tainting kernel
[  205.983895] RTW: rtl8822bu v5.1.0-5_17968.20160601_BTCOEX20160411-1400_beta
[  205.983896] RTW: rtl8822bu BT-Coex version = BTCOEX20160411-1400
[  205.983931] usbcore: registered new interface driver rtl8822bu

```

---

### Post by franciscothekid on 2017-07-26
I put a pci express card in and it's worked straight out the box but i'd still like to get the usb adapter going.
Ive had to pull my video card to fit the pci express card in.



```
wlp3s0    IEEE 802.11  ESSID:"newnet"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: D0:17:C2:C4:E6:80   
          Bit Rate=15 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

lo        no wireless extensions.

enp4s0    no wireless extensions.

```

---

### Post by chili555 on 2017-07-26
It loads without drama; let's also see: ```
dmesg | grep -i -e rtl -e wlx
```

---

### Post by franciscothekid on 2017-07-26
```
\[    2.483812] r8169 0000:04:00.0 eth0: RTL8168g/8111g at 0xffffaf7b418b1000, 1c:1b:0d:c6:a8:61, XID 0c000800 IRQ 29
[   11.557813] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   11.565417] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.565623] rtlwifi: rtlwifi: wireless switch is on
[   11.595263] rtl8192ce 0000:03:00.0 wlp3s0: renamed from wlan0

```

---

### Post by praseodym on 2017-07-27
Lets try updating "rtlwifi":
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms
```
Worked without errors? Then reboot

---

### Post by chili555 on 2017-07-27
Which one are we trying to help you troubleshoot??

I'm confused.

---

### Post by franciscothekid on 2017-07-27
```
Error! Bad return status for module build on kernel: 4.10.0-27-generic (x86_64)
Consult /var/lib/dkms/rtlwifi-new/0.10/build/make.log for more information.
```

---

### Post by franciscothekid on 2017-07-27
asus

---

### Post by jeremy31 on 2017-07-27
Hi chili555
Have you tried my version in kernel 4.10?  I think Brandon made a mistake when he added this device and added it as an 8812 device instead of the 8822B and one of the issues reported supports my theory
[https://github.com/brandon-bailey/rtl8822bu/issues/2](https://github.com/brandon-bailey/rtl8822bu/issues/2)

---

### Post by chili555 on 2017-07-27
> **jeremy31 said:**
> Hi chili555
Have you tried my version in kernel 4.10?  I think Brandon made a mistake when he added this device and added it as an 8812 device instead of the 8822B and one of the issues reported supports my theory
[https://github.com/brandon-bailey/rtl8822bu/issues/2](https://github.com/brandon-bailey/rtl8822bu/issues/2)It compiles with warnings but no errors in 4.10. From modinfo:

```
filename:       /home/chili/Desktop/Forum/rtl8822bu/8822bu.ko
version:        v5.1.0-5_17968.20160601_BTCOEX20160411-1400_beta
author:         Brandon Bailey <brandondanielbailey@gmail.com>
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5BD8B5BDDE5F15D44C8C01E
alias:          usb:v0BDApB82Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v[COLOR="#FF0000"]0B05[/COLOR]p[COLOR="#FF0000"]184C[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1812d*dc*dsc*dp*ic*isc*ip*in*
<snip>

```And in the code:

```
#ifdef CONFIG_[COLOR="#FF0000"]RTL8822B[/COLOR]
	/*=== Realtek demoboard ===*/
	{USB_DEVICE(0x0B05, 0x1812), .driver_info = RTL8812}, /* ASUS - Edimax */
	{USB_DEVICE(0x7392, 0xB822), .driver_info = RTL8822B}, /* Edimax - EW-7822ULC */
	{USB_DEVICE(0x[COLOR="#FF0000"]0b05[/COLOR], 0x[COLOR="#FF0000"]184c[/COLOR]), .driver_info = RTL8822B}, /* ASUS USB AC53 */
	{USB_DEVICE_AND_INTERFACE_INFO(USB_VENDER_ID_REALTEK, 0xB82C, 0xff, 0xff, 0xff), .driver_info = RTL8822B}, /* Default ID */
#endif /* CONFIG_RTL8822B */
```

---

### Post by chili555 on 2017-07-27
> **franciscothekid said:**
> asusHowever, you have the PCIe card inserted and the drivers probably conflicting making troubleshooting very difficult.

Frankly, the USB is so new and the driver is so new that I have my doubts that we'll get it working smoothly for now. Our colleagues Jeremy and praseodym may have another idea.

---

### Post by Bucky Ball on 2017-07-28
> **chili555 said:**
> However, you have the PCIe card inserted and the drivers probably conflicting making troubleshooting very difficult.

+1.

---

### Post by franciscothekid on 2017-07-29
Thank u everybody for all the help and suggestions. It's a great community we have here.
Ended up swapping the video card. Have sacrificed a bit of gpu computing power for wireless connectivity.
The pci express card works fine.

---

### Post by Y2J on 2017-11-03
Please help!

I am following this guide for installing EW-7822ULC USB nano: 
[https://github.com/brandon-bailey/rtl8822bu](https://github.com/brandon-bailey/rtl8822bu)

Ubuntu 17.10

```
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-16-generic/build M=/home/yosuif/Downloads/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-16-generic'
  CC [M]  /home/yosuif/Downloads/rtl8822bu/core/rtw_cmd.o
In file included from /home/yosuif/Downloads/rtl8822bu/include/drv_types.h:32:0,
                 from /home/yosuif/Downloads/rtl8822bu/core/rtw_cmd.c:22:
/home/yosuif/Downloads/rtl8822bu/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/yosuif/Downloads/rtl8822bu/include/osdep_service.h:345:2: error: implicit declaration of function &#8216;allow_signal&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/home/yosuif/Downloads/rtl8822bu/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/home/yosuif/Downloads/rtl8822bu/include/osdep_service.h:355:6: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
  if (signal_pending(current))
      ^~~~~~~~~~~~~~
      timer_pending
/home/yosuif/Downloads/rtl8822bu/include/osdep_service.h:356:3: error: implicit declaration of function &#8216;flush_signals&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
cc1: some warnings being treated as errors
scripts/Makefile.build:302: recipe for target '/home/yosuif/Downloads/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/yosuif/Downloads/rtl8822bu/core/rtw_cmd.o] Error 1
Makefile:1546: recipe for target '_module_/home/yosuif/Downloads/rtl8822bu' failed
make[1]: *** [_module_/home/yosuif/Downloads/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-16-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$
```

```
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$  sudo make install
install -p -m 644 8822bu.ko  /lib/modules/4.13.0-16-generic/kernel/drivers/net/wireless/
install: cannot stat '8822bu.ko': No such file or directory
Makefile:1324: recipe for target 'install' failed
make: *** [install] Error 1 
```

---

### Post by chili555 on 2017-11-03
> **Y2J said:**
> Please help!

I am following this guide for installing EW-7822ULC USB nano: 
[https://github.com/brandon-bailey/rtl8822bu](https://github.com/brandon-bailey/rtl8822bu)

Ubuntu 17.10

```
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-16-generic/build M=/home/yosuif/Downloads/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-16-generic'
  <snip>
make[1]: *** [_module_/home/yosuif/Downloads/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-16-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$
```

```
yosuif@yosuif-Z87-D3HP:~/Downloads/rtl8822bu$  sudo make install
install -p -m 644 8822bu.ko  /lib/modules/4.13.0-16-generic/kernel/drivers/net/wireless/
install: cannot stat '8822bu.ko': No such file or directory
Makefile:1324: recipe for target 'install' failed
make: *** [install] Error 1 
```For your benefit and all of the searchers, when 'make' ends in an error, there is no point in continuing as all further steps will fail also. 

I suggest that you try this:

```
cd ~/Downloads
rm -rf rtl8822bu
git clone https://github.com/stylpen/rtl8822bu.git
cd rtl8822bu
make
sudo make install
sudo modprobe 8822bu
```

---

### Post by Chronon on 2018-03-27
Thank you!  I was using another driver previously, but it broke a few months back when I upgraded to a new kernel.

After further testing it seems to have a couple of bugs.  I'm using 4.14.25 kernel and building a 32-bit module.

1) 5 GHz hardware doesn't seem to be enabled.
2) After waking from suspend, the AC53-Nano doesn't wake up correctly.  Rebooting makes it work again.  (Next time I'll try reloading the module.)

---

### Post by tammojsmit on 2018-11-20
Since the wireless card is missing from the laptop, I use a ASUS AC53 nano dongle, which always works with windows (I dual-boot). In the past I was able to use the fix provided by jeremy31 with success. Every time Xubuntu updated, I would have to reinstall the package, and it would work wonderfully until the next update. However, the last update has blocked me, and I get errors when trying to install. It seems like it doesn't like the driver. Any ideas? Oh, and, if I close the lid and then reopen, I would have to restart Xubuntu (Bionic Beaver).

---

