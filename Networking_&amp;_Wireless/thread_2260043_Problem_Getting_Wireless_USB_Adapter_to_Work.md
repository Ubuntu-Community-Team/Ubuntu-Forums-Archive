---
title: "Problem Getting Wireless USB Adapter to Work"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by iconick on 2015-01-08
Hello all,

I am new to Ubuntu and have been searching a lot of old posts for an answer to my problem, but I am not quite finding a solution and thought I'd post my situation.

I have just installed Ubuntu onto my old desktop computer by using a usb. The problem is that it requires a wireless usb adapter to connect to the internet as the router is too far away. Mine specifically is the Netgear N600 Wireless Dual Band USB Adapter. I think I should install a driver called ndiswrapper but am having problems even doing that. 

Any input would be very appreciated. Thanks.

---

### Post by iconick on 2015-01-08
I am posting from a laptop that has working internet connection.

In advance, I typed the command: lsusb and this is what I got for the wireless adapter:

Bus 002 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

---

### Post by chili555 on 2015-01-08
From the desktop upon which ndiswrapper and the USB will peacefully reside, please run and post:```
lsb_release -d
uname -r
```These outputs should be pretty brief, so you can jot them down and post them.

---

### Post by iconick on 2015-01-09
> **chili555 said:**
> From the desktop upon which ndiswrapper and the USB will peacefully reside, please run and post:```
lsb_release -d
uname -r
```These outputs should be pretty brief, so you can jot them down and post them.

Hi thanks for responding so like type them into terminal? Also I don't think I have ndiswrapper yet?

I got:

lsb release -d
Description: Ubuntu 14.10

uname -r
3.16.0-23-generic

---

### Post by chili555 on 2015-01-09
>  I don't think I have ndiswrapper yet?That's why the doctor is here!

Please download these packages on any computer: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.59-2_all.deb)

We also need to know if the desktop is 32- or 64-bit; learn:```
arch
```If 32-bit (i686), download this: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_i386.deb) and if 64-bit (x86_64),then this: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.59-2_amd64.deb) 

You will also need the Windows XP inf and sys files for the device: [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173) Please see post #6. When you have all the files, transfer them on a USB stick or similar to the desktop of the desktop! Har har har!!

Now on the desktop machine, install ndiswrapper from the terminal:```
cd ~/Desktop
sudo dpkg -i ndis*
```Now, right-click the driver package and select 'Extract Here.' Now, back to the terminal:```
cd ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2_amended
sudo ndiswrapper -i bcmn43xx[COLOR="#FF0000"]??[/COLOR].inf
```Where ?? is either 32 or 64 depending on your architecture. Then do:```
sudo ndiswrapper -ma
sudo depmod -a
sudo modprobe ndiswrapper
```Unless there is an error, the wireless should be working.

---

