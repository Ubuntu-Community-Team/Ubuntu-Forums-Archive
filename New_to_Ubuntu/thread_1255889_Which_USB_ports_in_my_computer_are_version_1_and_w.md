---
title: "Which USB ports in my computer are version 1 and which are version 2?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-02
Hello,
When I turn on my computer I see some text indicating that I have USB ver1 (or was it 1.1?) and some USB version 2. I have 2 USB ports on the front of the computer and 6 or 8 at the back of the computer. How can I tell which is which?

Thanks.

---

### Post by Mark Phelps on 2009-09-02
This is typically determined by BIOS settings.  If your motherboard provides USB 2.0 port capability, that is the default for all ports unless you modify the BIOS settings.

One way to check is to get a USB 2.0 device (USB Stick) and plug it into the ports, one at a time.  If the port is set for USB 1.1, you should get a popup indicating that you will get better performance if you set it for USB 2.0.

---

### Post by LewRockwell on 2009-09-02
it should also be noted, for present and future visitors to this thread, that some mainboard(motherboard) level USB ports will "only" ever be 1.1 due to the firmware(BIOS) configuration and, in some cases, actual board level hardware speed limitations

in the case of desktops this can be overcome by adding a 2.0 USB PCI card

in the case of laptops this can be overcome by adding a 2.0 USB PCMCIA card

in today's market, both of these devices are readily available new and used


also note that certain USB devices which have "heavy" power consumption should only be purchased/utilized if they have stand-alone power supplies included in the design and accompanying the device at point-of-sale

the USB power bus can only accomodate a certain maximum accumulated wattage of USB-powered devices and if this is exceeded then one or more devices may fail and/or under-perform and/or may exhibit strange behaviour

as always, your mileage may vary...buyer be aware and buyer beware...

we now return you to your regularily scheduled programming

.

---

### Post by hanzj on 2009-09-02
mark,
You wrote:
>  If your motherboard provides USB 2.0 port capability, that is the default for all ports unless you modify the BIOS settings.
1. I don't think I modified my BIOS USB settings. 
2.  have plugged in a USB 2.0 device (iPod video, 5.5 generation) into almost all USB ports and I don't receive the message. Is there a way to confirm (say, via a command in terminal) whether indeed all ports are USB 2.0?

---

### Post by hanzj on 2009-11-04
The usb ports on the front of the computer seem to have faster speeds, based on the "File Operations" window that pops up when I'm moving/copying to a USB device.

But I want to confirm this

---

