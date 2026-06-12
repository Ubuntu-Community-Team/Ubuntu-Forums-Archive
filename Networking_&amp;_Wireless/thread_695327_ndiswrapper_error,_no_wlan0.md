---
title: "ndiswrapper error, no wlan0"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by Speedoo on 2008-02-12
Hi folks,
I finally got tired of constantly reconnecting dropped wireless connections with my rtl8187 driver.  My chipset is Realtek OBDA:8187.  The general recommendation is ndiswrapper with the Win98 driver.  But when I installed this, I get no connectivity (in fact, no wlan0 at all) and this error in the relevant portion of dmesg:

[   17.724000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   17.888000] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[   18.040000] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[   18.040000] ndiswrapper (mp_init:216): couldn't initialize device: C0010006
[   18.040000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   18.040000] ndiswrapper (mp_halt:259): device f793a500 is not initialized - not halting
[   18.040000] ndiswrapper: device eth%d removed
[   18.040000] ndiswrapper: probe of 1-6:1.0 failed with error -22
[   18.040000] usbcore: registered new interface driver ndiswrapper
[


When I do ndiswrapper -l I get:

net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

(despite the fact that rtl8187 is now blacklisted in modprobe.d)
I've seen this problem posted before, but never answered successfully, so I thought I'd try again.
Thanks for any help!

---

### Post by darkmdbeener on 2008-02-12
mined sendin me the answer i think are two ? are related 

mine say alternate bcm43xx instead 

so if you dont mind post it in here or send me a pm thanks
[http://ubuntuforums.org/showthread.php?t=695288](http://ubuntuforums.org/showthread.php?t=695288)


my fix was
sudo apt-get --reinstall install linux-ubuntu-modules-2.6.22-14-generic    
 
i dont know if that can help you

---

### Post by Speedoo on 2008-02-16
bump.

Getting really frustrated with my rtl8187!

Thanks in advance for any suggestions,

---

### Post by Speedoo on 2008-05-19
bump

---

