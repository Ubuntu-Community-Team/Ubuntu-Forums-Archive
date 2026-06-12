---
title: "Getting a working wifi Logilink 802.11ac Nano USB Adapter WL0237 (Realtek RTL8812AU)"
date: 2016-06-11
forum: Networking &amp; Wireless
---

### Post by jaleks2 on 2016-06-11
After having had problems with the above mentioned wifi adapter I finally found a work around to get it running and thought I'd share it.
The problem had been, that the Realtek drivers which came with the wireless LAN adapter compiled fine (driver version rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51, kernel version 3.2.0-3-686-pae) and installed, but the adapter was only recognized as USB not as wifi adapter.

With help from an older thread here in the forum, I had a look to 'modinfo 8821au' which included a list of aliases the driver would work for.
Unfortunately, mine was not among them, a 'lsusb' showed "Bus 002 Device 006: ID 0bda:a811 Realtek Semiconductor Corp." for my adapter.
Having a grep into the source I found a line where a similar ID was present: 'os_dep/linux/usb_intf.c +304'. This line looked similar to my ID, (it was "{USB_DEVICE(USB_VENDER_ID_REALTEK, 0x0811),.driver_info = RTL8821},/* Default ID */"), so I changed "0x0811" to "0xA811", did all the compiling and installing again, and when I plugged in my wifi adapter, it was recognized and now both of the internal interfaces are shown with 'ifconfig'.

---

