---
title: "Ralink 2500 drivers problem"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by CoG on 2007-02-14
Hello, I cant configure my wireless device conceptronic c54ru in mode monitor:

This is what I get:

linux@linuxpc:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz
          RTS thr:off   Fragment thr=2346 B

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B

sit0      no wireless extensions.

and:

linux@linuxpc:/$ sudo airmon-ng


Interface       Chipset         Driver

wmaster         Unknown         Unknown (MONITOR MODE NOT SUPPORTED)
wlan0           Unknown         Unknown (MONITOR MODE NOT SUPPORTED)


linux@linuxpc:/$ lsusb
Bus 001 Device 082: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 14b2:3c22
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

linux@linuxpc:/$ lsmod | grep rt
rt2570                198208  0
parport_pc             37796  0
parport                39496  2 parport_pc,lp
rt73usb                37888  0
80211                 175880  2 rate_control,rt73usb
crc_itu_t               3200  1 rt73usb
agpgart                34888  2 intel_agp
usbcore               134912  5 rt2570,rt73usb,usbhid,uhci_hcd

linux@linuxpc:/$ modinfo rt2500
filename:       /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rt2500.ko
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2005/07/10
license:        GPL
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
srcversion:     74C1EE2A4556CB962AF4434
parm:           ifname:Network device name (default eth%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)


PLEASEEEEEEEEEE HELPPPPPPPPPP

Is the good driver loaded? please help I dont know what ese I can do.

---

### Post by whayong on 2007-02-16
I bought a new mPCI card with the RT2500 chipset since it says that this works well with Edgy.  I just finished installing it in my laptop a few minutes ago and ran into similar problems.  I have yet to search around for it but you should be able to download the driver here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

I don't know what to do with it, or put it after downloading it though, lol!

---

### Post by bionnaki on 2007-02-16
see if the how-to in my sig works.

---

### Post by whayong on 2007-02-19
Your how to didn't work for me.  lshw doesn't return RT2500, instead it returns as Ralink unknown device 0302.

I went ahead and followed the how to anyway, result, wireless card disappeared from ifconfig and iwconfig.  I just did a fresh install right now.

---

