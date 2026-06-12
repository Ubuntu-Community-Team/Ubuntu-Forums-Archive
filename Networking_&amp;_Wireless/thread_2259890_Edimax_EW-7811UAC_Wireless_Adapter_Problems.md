---
title: "Edimax EW-7811UAC Wireless Adapter Problems"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by customcomputersbydan on 2015-01-07
Hello all, 
I recently purchased an Edimax EW-7811UAC usb wifi adapter, and I am currently attempting to get it working in Kubuntu 14.04. I'm pretty sure it's running on the Realtek RTL 8812AU chipset, and so I attempted to follow this guide: [http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244) . However, after much mucking around with the modules (I did get the 8812au.ko module to actually show itself as running), the adapter still won't function with the driver. I believe the problem is that the adapter isn't being recognized as a wireless device. If I run lsusb, I get this output: 
**Bus 002 Device 002: ID 7392:a813 Edimax Technology Co., Ltd **                                                                                   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                                 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                 
Bus 001 Device 004: ID 1740:9603 Senao RTL8188S WLAN Adapter                                                                                   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                                 
Bus 003 Device 003: ID 03f0:1604 Hewlett-Packard DeskJet 940c                                                                                  
Bus 003 Device 004: ID 413c:2001 Dell Computer Corp. Keyboard HID Support                                                                      
Bus 003 Device 002: ID 413c:1001 Dell Computer Corp. Keyboard Hub                                                                              
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
The adapter is listed in bold (the Senao adapter is the one I'm currently using). How do I make the adapter recognized as a network device, so that the driver can be used for it? Everything in this distro is fully updated, and I'm stumped. Any and all advice would be greatly appreciated, so thanks in advance! :-)

---

### Post by chili555 on 2015-01-07
Please notice that the device mentioned in the thread you linked is:> Bus 001 Device 005: ID [COLOR="#FF0000"]7392:a811[/COLOR] Edimax Technology Co., LtdAnd you said your device is:> Bus 002 Device 002: ID [COLOR="#FF0000"]7392:a813[/COLOR] Edimax Technology Co., Ltd a811 is not the same as a813 in driver-land.

Let's see what devices that 8812au claims:```
modinfo rtl8812au/8812au.ko
filename:       /home/chili/rtl8812au/8812au.ko
version:        v4.2.2_7502.20130517
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     26CD1F3E2157FD984CB5670
alias:          usb:v0846p9052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3314d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp0811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p805Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3316d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3315d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1058p0632d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3426d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0408d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0952d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp881Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8812d*dc*dsc*dp*ic*isc*ip*in*
<snip>
```I see A811 and A812 but not A813. That suggests two possibilities; first, that you have a new device, unseen previously, or that you made a typographical error when you copied your lsusb in your post.

Can you please confirm that you actually have:> 7392:[COLOR="#FF0000"]**a813**[/COLOR] Edimax Technology Co., Ltd If so, we have a new device and some serious tinkering to do!


------------------

Note for chili: rtl8812au/os_dep/linux/usb_intf.c

---

### Post by customcomputersbydan on 2015-01-07
Hey, thanks a ton for the quick response! :-) Yes, that is indeed a direct copy/paste from the Terminal, and it is indeed a813. I didn't realize it wasn't covered under those drivers.... Hmm, curiouser and curiouser... Maybe it's a new revision of that adapter...

---

### Post by chili555 on 2015-01-07
I propose a highly experimental technique. I suggest we add the device ID to the code and recompile the driver. It may work well, partially or not at all. First, we clean out the old driver:```
cd ~/rtl8812au
sudo make uninstall
make clean
```Now, we modify the C code:```
sudo gedit os_dep/linux/usb_intf.c 
```Use nano or kate or leafpad if you don't have the text editor gedit. At line 288, add a new entry:```
/*=== Customer ID ===*/
	{USB_DEVICE(0x7392, 0xA811),.driver_info = RTL8821}, /* Edimax - Edimax */
	{USB_DEVICE(0x7392, 0xA812),.driver_info = RTL8821}, /* Edimax - EW-7811UTC */
        [COLOR="#FF0000"]{USB_DEVICE(0x7392, 0xA813),.driver_info = RTL8821}, /* Edimax - EW-7811UAC */[/COLOR]
	{USB_DEVICE(0x2001, 0x3314),.driver_info = RTL8821}, /* D-Link - Cameo */
	{USB_DEVICE(0x0846, 0x9052),.driver_info = RTL8821}, /* Netgear - A6100 */
```Spacing, indentation, spelling, etc. must be perfect. Save and close the text editor. Now, recompile:```
make
sudo make install
```Reboot and let us hear your report.

---

### Post by customcomputersbydan on 2015-01-07
Ooh, I'll try it... :-) Thanks!

---

### Post by customcomputersbydan on 2015-01-07
It works!!! Thanks a ton! :-)

---

### Post by chili555 on 2015-01-08
Awesome! Don't forget that when a new kernel version is installed by Update Manager, you will need to recompile:```
cd ~/rtl8812au
make clean
make
sudo make install 
sudo modprobe 8812au
```Please retain the file and these instructions for that time.

---

