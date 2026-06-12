---
title: "comfast cf wu825n on ubuntu 18.04 which software runs the device?"
date: 2020-07-05
forum: Networking &amp; Wireless
---

### Post by ubto66 on 2020-07-05
the wifi card is able to run on trisquel 8 kernel version 4.4.0 178 suggesting it
can run on free software, cf free software foundation. I have also tested
the usb wifi card on ubuntu 18.04 kernel version 4.15.0 109 and
it runs. It has a rtl8192cu chip. Pidvid 0bda8178. Can you tell which
pieces of software on ubuntu 18.04 makes the wifi run? Are
they free software? Thanks.

---

### Post by chili555 on 2020-07-05
```
$ modinfo rtl8192cu | grep 8178
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8178[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```It is clear that the driver rtl8192cu and its associated firmware drive your device. They are free and open source software.

The device, driver and firmware then require several other pieces of software to actually connect; among them include Network Manager, wpa_supplicant, networkd and several others. They are all free and open source software.

---

### Post by praseodym on 2020-07-05
```
modprobe -c | grep -i "0bda.*8178"
alias usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8178[/COLOR]d*dc*dsc*dp*ic*isc*ip*in* rtl8192cu
alias usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8178[/COLOR]d*dc*dsc*dp*icFFiscFFipFFin* rtl8xxxu
```
Ubuntu ships two drivers, regularly, both are loaded, then it doesn't work because of driver conflicts. Blacklist the older rtl8192cu:
```

echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/blacklist-rtl8192cu.conf
```
and reboot.

```
lsmod

```
should only show **rtl8xxxu** then

---

### Post by ubto66 on 2020-07-08
> driver rtl8192cu and its associated firmware

Do you know how to get the source software? Or who could tell me where
to get the source software?

rtl8xxx will it make
any of these chips run?

---

### Post by chili555 on 2020-07-08
I believe that you can install the package linux-source and examine the code directly. Please be aware, however, that if you decide to make any changes to, perhaps tweak your wireless performance, that you will need to recompile the kernel; a fairly complicated task best left to those who are quite advanced. Despite my llong service to Linux and Ubuntu, I have never successfully compiled my own kernel. 

As for the firmware, it is located in /lib/firmware. I don't know how to examine it to see exactly what it does and doesn't do. You can see what firmware is called by the driver
with the terminal command:
```
modinfo rtl8xxxu | grep firm
```Your 0BDA:8178 device is one of the rare few that are claimed by two probably conflicting drivers: rtl8192cu and rtl8xxxu as my esteemed colleague @praseodym has reminded me. We have learned by experimentation that rtl8xxxu works best.

---

