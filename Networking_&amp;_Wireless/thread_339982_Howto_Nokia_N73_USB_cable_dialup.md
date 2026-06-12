---
title: "Howto: Nokia N73 USB cable dialup"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by niella on 2007-01-16
Good news for Noka N73 (and perhaps Nokia N80) users:

Using Edgy and kernel 2.6.20-rc5, I am able to perform a USB cable dialup with my Nokia N73 in "PC suite" mode.

With the current Edgy kernel (linux-headers-2.6.17-10), I get a crash with "kernel BUG at mm/slab.c:594!". This is described at [http://bugzilla.kernel.org/show_bug.cgi?id=7614](http://bugzilla.kernel.org/show_bug.cgi?id=7614)

To get it right simply
1. Compile the kernel 2.6.20-rc5 (See the Master Kernel Thread for info)

2. Plug the Nokia cable (mine is a CA-53) into the USB port.

3. From dmesg output, you should get
[  360.580000] cdc_acm 2-2:1.8: ttyACM0: USB ACM device
[  360.636000] usbcore: registered new interface driver cdc_acm
[  360.636000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  485.792000] cdc_acm 2-2:1.8: ttyACM0: USB ACM device

4. Simply set up wvdial.conf to use this device for your dialup...

Wala!

Niel

---

### Post by AndyGZA on 2007-02-02
Hi Niel, I posted this question on the forums the other day ([http://ubuntuforums.org/showthread.php?t=350109&highlight=nokia+n80+pc+suite)](http://ubuntuforums.org/showthread.php?t=350109&highlight=nokia+n80+pc+suite)), and just noticed your post here now. Do you think I'm having the same problem as you were? If so, please can you tell me how I should go about Compiling the kernel 2.6.20-rc5... I'm new to ubuntu and linux so *See the Master Kernel Thread for info* didn't help me all that much.

Thanks

Andy

---

### Post by daka on 2007-08-27
THANKS so much... lots of searching and experimenting but now your solution is really simple and it is working for my Nokia N80i (without touching the kernel):

Feisty

1. Plug the Nokia cable  into the USB port.. select PC Suite.

3. From dmesg output, you should get
[   17.452000] cdc_acm 1-2:1.8: ttyACM0: USB ACM device


4. Simply set up wvdial.conf to use this device for your dialup...
using as modem /dev/ttyACM0

here is my wvdial.conf file

[Dialer N80]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyACM0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","ac.vodafone.es";

Thanks again

Daka

---

