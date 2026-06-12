---
title: "Trying to use USB net adapter, but can't find usb0"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by Brian Kendig on 2006-08-01
I have a Gateway Astro all-in-one PC which, astonishingly, has no network port and no way to add one. I've installed Xubuntu 6.06 and I'm trying to use a Linksys USB200M wired adapter with it, but I'm doing something wrong.

When I boot up, 'network-admin' doesn't see the USB adapter, and 'ifconfig' only shows 'lo'.

I run 'sudo modprobe usbnet'. I get a prompt back, no errors or other messages.

'network-admin' still doesn't see the USB adapter. 'ifconfig' still shows only 'lo'.

'ifconfig usb0 192.168.2.2 netmask 255.255.255.0 up' only returns 'usb0 not found'.

What am I missing?

---

### Post by Brian Kendig on 2006-08-02
/etc/network/interfaces only contained an entry for lo; I added these lines to it:

iface usb0 inet dhcp
allow-hotplug usb0

and then I rebooted, but usb0 was still not found and the USB network adapter still doesn't work. (It works fine with my TiVo, however, so this isn't a hardware problem.)

When I connect or disconnect the USB network adapter, a line appears in /var/log/syslog to indicate that the action was noticed by the operating system, but there's nothing in there about the device being recognized as a network adapter.

What package do I need to install to enable Ubuntu 6.06 to use a USB network adapter?

---

### Post by GodsMoon on 2006-12-20
From what I gather Linksys changed the chip set for the usb200m when they switched to usb 2.0 so it no longer works in the 2.6.17 kernel.

They've updated the usbnet asix drivers that the usb200m uses in new versions of the kernel.

I works great under the 2.6.19 kernel but I don't know how to update the kernel with out messing everything up.

If anybody has any ideas let me know.

---

