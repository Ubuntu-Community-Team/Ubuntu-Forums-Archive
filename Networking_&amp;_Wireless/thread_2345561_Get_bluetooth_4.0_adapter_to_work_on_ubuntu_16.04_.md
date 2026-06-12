---
title: "Get bluetooth 4.0 adapter to work on ubuntu 16.04 laptop with pre-existing 2.0 module"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by schmeve on 2016-12-05
Hi all,

I recently bought bluetooth headphones that run on bluetooth 4.x and then found out my lenovo x201 only has bluetooth 2.x, so they're not compatible. 

I checked the list of previously working USB adapters [here ]("https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters#IO_Gear")and got the io gear GBU521W6 Bluetooth 4.0 USB Micro Adapter that seemed to work "out of the box" in earlier ubuntu versions - they do not work out of the box with mine (my headphones don't connect).

However, I am assuming this has something (or everything) to do with the fact that there is already a working bluetooth module in the laptop that the system recognises and uses. 

How do I get the system to recognise the dongle and use it instead of the built-in adapter?

I am very new to ubuntu and linux, so step-by-step, explain-it-like-I'm-5 instructions would be greatly appreciated. Thank you.

---

### Post by jeremy31 on 2016-12-05
Before getting too worried, try the workarounds they have at [https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197)

It would surprise me if the bug is more of a problem and you may not need the GBU521 and will likely lose it because of its size, I haven't seen mine in months but I did find my GBU421

If you want help disabling the internal post results for ```
lsusb
```
Enter the code in terminal, shortcut is CTRL + t, you can copy, cut, paste with the right mouse button

---

