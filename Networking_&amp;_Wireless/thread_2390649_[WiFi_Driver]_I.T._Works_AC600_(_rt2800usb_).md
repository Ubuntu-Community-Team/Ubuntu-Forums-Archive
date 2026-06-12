---
title: "[WiFi Driver] I.T. Works AC600 ( rt2800usb )"
date: 2018-05-01
forum: Networking &amp; Wireless
---

### Post by raibtoffoletto on 2018-05-01
Hey Guys,

I'm coming here as a last resource because it seems that no one on the web was able to solve this problem.

I bought a WiFi USB-Dongle from " I.T. Works" (company who seems to sell products only for France/BeNeLux) and it doesn't work on Linux.

I'm going bald trying to make it work, the driver it uses is the **rt2800usb**, which has already been supported by the kernel for years!

What happens is that this stupid company somehow uses a Vendor/Product id that is unknown to mankind :

```
 Bus 002 Device 004: ID 148f:fffe Ralink Technology, Corp. 
```

So my question is... is there anyway to make an alias to modprob recognize this device to be used with the **rt2800usb** ???

Or any other make it recognizable ?? Hacking the vendor/product ID ?? 

Or should I just admit defeat and realize I lost 30&#8364; in a scam... com'on, it is 2018, companies should not be doing this kind of stuff.


The system I'm using now: Ubuntu 18.04 // MATE flavour // 4.15.0-20-generic


Thanks for any help!!

---

### Post by Yellow Pasque on 2018-05-01
You would probably need to find a way to add it to the table here: [https://github.com/torvalds/linux/blob/master/drivers/net/wireless/ralink/rt2x00/rt2800usb.c#L1102](https://github.com/torvalds/linux/blob/master/drivers/net/wireless/ralink/rt2x00/rt2800usb.c#L1102)

---

### Post by jeremy31 on 2018-05-01
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2018-05-01
> I'm going bald trying to make it work, the driver it uses is the rt2800usb, Can you please show us a citation? My Google-foo suggests that it is not supported by *anything*!

---

### Post by raibtoffoletto on 2018-05-03
So, I looked at the $indows drivers that came in a mini CD and there I've found this info:

> 
 rt2870.infRalink RT2870 series USB Wireless LAN Card.


So looking up on Google, it return me that this driver is part of the RT2870.
As stated by the Debian Wiki: [https://wiki.debian.org/rt2800usb](https://wiki.debian.org/rt2800usb)

So I imagine if using the linux version of the driver should make it work, right?
It only need to be recognised by the system to use this specific one. 

Ps: I've tried ndiswrapper without success.

---

### Post by raibtoffoletto on 2018-05-03
> **Temüjin said:**
> You would probably need to find a way to add it to the table here: [https://github.com/torvalds/linux/blob/master/drivers/net/wireless/ralink/rt2x00/rt2800usb.c#L1102](https://github.com/torvalds/linux/blob/master/drivers/net/wireless/ralink/rt2x00/rt2800usb.c#L1102)

I'll propose a modification soon I can certified it works.

---

### Post by raibtoffoletto on 2018-05-06
So... I guess the only way to test is to compile my own Kernel version with the modification?
No easier way to add the Vend/Dev ID to the driver list?

---

### Post by jeremy31 on 2018-05-06
There are ways to build a single kernel module and put it in the /lib/modules/ directory
You have to enable source code repos in the Software and Updates, download kernel source, make changes to the file you want, copy the .config and Module.symvers from /usr/src/linux-headers for the kernel you are using
From the source code directory /drivers/net/wireless/ralink/rt2x00
```
cp /usr/src/linux-headers-$(uname -r)/.config .
cp /usr/src/linux-headers-$(uname -r)/Modules.symvers .
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```
Look at terminal results for ```
modinfo rt2800usb | grep filename
```
and use a command like
```
sudo cp rt2800usb /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/
```
to copy it into the kernel module directory then update the system for the ID you entered
```
sudo depmod -a
```
Reboot and see if it worked.  You will need Secure Boot disabled if it is an UEFI install

---

