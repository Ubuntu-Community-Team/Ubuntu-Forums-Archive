---
title: "D-Link DWA-140 rev D1 on ubuntu 13.10 (may be for others as well)"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by kiul on 2014-02-08
Hi there,

I've found that [D-Link DWA-140 rev D1]("https://wikidevi.com/wiki/D-Link_DWA-140_rev_D1") does not work with any kernel version but the 3.13 one, as pointed out in

[https://wikidevi.com/wiki/User:X64/Linux_kernel_wireless_device_support](https://wikidevi.com/wiki/User:X64/Linux_kernel_wireless_device_support)

So, take into account updating your system to kernel 3.13 in order to correctly set up such a wireless USB device.

The kernel was recently released and can easily be installed following this [link]("http://yoyo308.com/2014/01/20/kernel-3-13-estable-disponible-instalacion-en-ubuntu-linux-mint-y-derivadas/"). 

In summary:

for 32bit
[COLOR=#3F3F3F][FONT=Consolas]
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_i386.deb)[/FONT][/COLOR]

[COLOR=#3F3F3F][FONT=Consolas]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb)[/FONT][/COLOR]

[COLOR=#3F3F3F][FONT=Consolas]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_i386.deb)


for 64 bit:


[COLOR=#3F3F3F]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)[/COLOR]

[COLOR=#3F3F3F]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-headers-3.13.0-031300_3.13.0-031300.201401192235_all.deb)[/COLOR]

[COLOR=#3F3F3F]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/linux-image-3.13.0-031300-generic_3.13.0-031300.201401192235_amd64.deb)[/COLOR]
[/FONT][/COLOR]


and the install via:

sudo  dpkg -i linux-headers-3.13.0-*.deb linux-image-3.13.0-*.deb


After this installation reboot the PC, and then check for this output in your terminal:

lsmod | grep ^rt

rt2800usb              27225  0 
rt2x00usb              20886  1 rt2800usb
rt2800lib              95492  1 rt2800usb
rt2x00lib              56124  3 rt2x00usb,rt2800lib,rt2800usb


If so, it means you are using the correct wireless kernel modules for D-Link DWA-140 rev D1. It works pretty good on ubuntu 13.10.
 
Best

---

