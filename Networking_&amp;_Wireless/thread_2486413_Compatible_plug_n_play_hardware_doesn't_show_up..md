---
title: "Compatible plug n play hardware doesn't show up."
date: 2023-04-29
forum: Networking &amp; Wireless
---

### Post by Evil Wayz on 2023-04-29
I have a comfast cf-935ax USB Wi-Fi dongle. 

I bought it after reading about it on github,  it was listed as plug n play for Linux above kernel  5.19.

I'm running 23.04 and the 6.2 kernel so it should work.  But it doesn't show up on inxI -Fxz only on lsusb as Mediatek.

I got it from China.   So before I start trouble shooting and building drivers,  I was wondering  if a DOA  USB device would still  show up as plugged in.

---

### Post by Evil Wayz on 2023-04-29
OK I did some modprobe witchcraft and now it works but the link light doesn't work in Ubuntu but it does in *******.

---

### Post by morrownr on 2023-04-30
Hi Evil Ways

> I was wondering if a DOA USB device would still show up as plugged in.

It depends on how the adapter is DOA. If the adapter can't power up then it won't show. If there is no driver or firmware, it will show with lsusb but will not show an interface.

The CF-953AX uses the Mediatek mt7921au tri-band chipset. I'm pretty sure that this is the first USB wifi chipset that had its driver in the Linux kernel before adapters were available to buy. The driver went into the kernel in spring of 2022. Adapters were available to buy in summer or 2022. The driver is called mt7921u and it requires two firmware files. It can take a while for distros to solidify support for new hardware. Ubuntu 23.04 with kernel 6.2 has the driver and firmware but sometimes companies use their own device ID (VID/PID) and until that device ID is added to the driver in the kernel, the driver will not recognize the device. I work with users to try to confirm and send patches into the kernel as soon as possible.

If you go to the following site and select menu item 2,

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

...scroll down to the cf-953ax adapter. The entry includes methods to get the adapter going even if you are not using a kernel yet that has the device ID. If any of the information is not correct, please let me know.

Some things to know:

Development on the mt7921u driver is still ongoing. P2P support is going into kernel 6.4. The new generation of tri-band adapters require drivers that are big and complex. I think it is really cool that us Linux users have USB wifi support for a tri-band adapter and my experience with the driver is that it is very solid and stable at this point. New firmware files are being released almost monthly these days. Remember that in-kernel drivers consist of 2 or more files--the driver that is in the kernel and the firmware files. The mt7921u requires two firmware files. Remember that the firmware files are not part of the kernel, they are part of the distro.

You can check the version of the firmware files as such:

$ ethtool -i <wlan0>

You may need to install 2 apps:

$ sudo apt install iw ethtool

Use iw to get the wifi interface:

$ iw dev

Replace <wlan0> with your wifi interface name.

At the USB-WiFi link I posted above, menu item 8 shows how to add or upgrade firmware files. Section 2 is above the mt8021au chipset.

I would appreciate it if you could run..

$ lsusb

... and post the device ID of your adapter so I can compare notes and keep the information at USB-WiFi current.

Thanks.

---

