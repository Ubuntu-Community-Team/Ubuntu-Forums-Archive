---
title: "What's new over at the USB-WiFi? - 2022-03-11"
date: 2022-03-11
forum: Networking &amp; Wireless
---

### Post by morrownr on 2022-03-11
The following repo is shown in the first sticky post so if you can't find this message in the future, go to that post:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

What's new?

It appears that a new USB WiFi chipset will be released in the not so distant future. How do we know? Driver support for the mt7921u chipset started flowing into the Linux kernel last week as shown in the linux-wireless list. The core mt7921 driver has been in the kernel since v5.12 and has supported PCIe and M.2 cards. Now USB support is being added. I have a little laptop that has a mt7921 based internal wifi card and when I installed Ubuntu 21.10, it just worked. The mt7921 chipset comes in WiFi 6 and WiFi 6e versions. This is very good news.

Other news?

Here is a link to a recently posted new 8821cu driver:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

If you have an adapter based on the 8811cu, 8822cu or 8831au chipsets, you might want to move over to this driver as it is good. I don't recommend Linux users buy new adapters with Realtek chipsets because the drivers are the wrong technology but if you have an existing adapter, this driver could be a good improvement to your system.

Regards

---

