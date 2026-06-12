---
title: "&quot;MediaTek Inc. 802.11 n WLAN&quot; adapter doesn't work"
date: 2024-11-03
forum: Networking &amp; Wireless
---

### Post by esflownk on 2024-11-03
This is my lsusb output:
```
Bus 002 Device 003: ID 0e8d:7603 MediaTek Inc. 802.11 n WLAN
```

The problem is that Ubuntu doesn't recognize the adapter, when I was on Windows, the adapter was recognized but it suddenly disconnected, although it was well connected, it disconnected when it was almost ready to connect in fact.

---

### Post by morrownr on 2024-11-03
Well, let me see. Here is the Mediatek kernel support site:

[https://wireless.docs.kernel.org/en/latest/en/users/drivers/mediatek.html](https://wireless.docs.kernel.org/en/latest/en/users/drivers/mediatek.html)

I see: MT7603E 802.11b/g/n 2T2R 2.4GHz PCIe chip

That means it is supported.

Paste the results of the following commands:

$ iw dev

$ lsmod | grep mt7

---

### Post by esflownk on 2024-11-04
None of the commands showed anything

---

### Post by morrownr on 2024-11-04
Hmmm...

This is a chip that has in-kernel driver support and you are not seeing the driver loading so maybe the firmware file is not installed in Ubuntu. Check the log and see if you can see anything related the driver:

$ sudo dmesg

---

### Post by jeremy31 on 2024-11-04
> **morrownr said:**
> Well, let me see. Here is the Mediatek kernel support site:

[https://wireless.docs.kernel.org/en/latest/en/users/drivers/mediatek.html](https://wireless.docs.kernel.org/en/latest/en/users/drivers/mediatek.html)

I see: MT7603E 802.11b/g/n 2T2R 2.4GHz PCIe chip

That means it is supported.

Paste the results of the following commands:

$ iw dev

$ lsmod | grep mt7

I am fairly sure the mt7603e driver is not for USB devices

---

### Post by esflownk on 2024-11-04
This is the $sudo dmesg log:
[ATTACH]294474[/ATTACH]

---

### Post by morrownr on 2024-11-04
> I am fairly sure the mt7603e driver is not for USB devices

Me too. The Mediatek list I posted does not show a USB version of the mt7603 chip.

However, I cannot explain the following:

[    1.033582] usb 2-1.1: New USB device found, idVendor=0e8d, idProduct=7603, bcdDevice= 0.01
[    1.033592] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.033596] usb 2-1.1: Product: 802.11 n WLAN
[    1.033599] usb 2-1.1: Manufacturer: MediaTek

@esflownk 

What version of Ubuntu are you using? And what kernel?

Can you shed some light on the device? You called the device an adapter. Do you mean USB WiFi adapter? If so, never heard of a usb device with that chip. This is a mystery.

---

### Post by esflownk on 2024-11-05
Ubuntu Operative System name:
Ubuntu 24.04.1 LTS

This is what "uname -r" command showed:
Linux esflownk 6.8.0-48-generic #48-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 14:04:52 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

(EXTRA) Firmware Version:
A05

And yeah, it's an USB WIFI adapter.

---

### Post by morrownr on 2024-11-05
> And yeah, it's an USB WIFI adapter.

I've been keeping up with usb wifi chips for many years and this one is one that I was unaware of. The mt7603u is simply not supported. The mt7603e is supported. I have no idea why this is. My recommendation is for you to take a look at the following site:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

That is the Main Menu for the site. Reading menu item 1 is a good idea and then you can see many adapters that will work plug and play in Ubuntu 24.04 under menu item 2, the Plug and Play List. You can ask questions in Issues at the site. 

Disclaimer: I am the owner of that site. I do not make any money from the site and I get a lot of help. The sites gets over 20k hits per week and if any bad information shows up, it gets called out rapidly. I think it will help in this case.

Good luck.

---

### Post by 1fallen on 2024-11-05
@morrownr We All owe you a big Thanks and the other's involved. :KS

---

### Post by morrownr on 2024-11-10
1fallen,

Thanks for the kind words. Stop by USB-WiFi anytime.

---

