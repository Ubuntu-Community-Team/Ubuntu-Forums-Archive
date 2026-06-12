---
title: "Odd Wireless Problem with HP DV2000 series laptop"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by k3eleven on 2007-09-17
I know that there may not be such a thing as an "odd" wireless problem in ubuntu, but i'll give it a try:

When i switch sources of power and then restart my laptop, my wireless will not work until i start up ubuntu a second time using that same source of power.

So for example, if i had my laptop plugged into the wall and was using ubuntu, and then i decided to take it with me to class, when i get into class and start up my laptop without the power connected into the wall, the wireless will not start up. I have to restart the laptop for my wireless to start up normally.

What i also thought was interesting, was that on a failed startup, my wireless light will turn blue at the ubuntu boot screen while it is loading the OS, but when the computer goes to the GDM login screen the light turns back to orange (off) at that point. So it must mean that something is loading at that point that breaks the wireless that is only loaded after the first time you switch booting under different power sources? But i am in no way familiar enough with the boot process to even begin to determine what that could be...

Does anyone have any idea what could be causing this? This wasn't a problem until a few weeks ago but i can't find any solutions for it on the internet.

For the record:

Laptop is an HP DV2315nr
im running fwcutter for bcm43xx drivers (i know, i know...)

the dmesg output when i start up the laptop and the wireless does not work:

```

[   26.280000] ACPI: Power Button (CM) [PWRB]
[   26.380000] ACPI: Battery Slot [BAT0] (battery present)
[   26.492000] wmi_add device=df845800
[   26.492000] calling WQBA
[   26.508000] pcc_acpi: loading...
[   26.720000] powernow-k8: Found 2 AMD Turion(tm) 64 X2  processors (version 2.00.00)
[   26.720000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[   26.720000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   28.548000] SoftMAC: Open Authentication completed with 00:18:39:db:ba:fc
[   30.456000] ppdev: user-space parallel port driver
[   33.056000] apm: BIOS not found.
[   35.240000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[   35.240000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[   35.240000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[   35.240000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[   38.696000] bcm43xx: IRQ_READY timeout
[   48.460000] bcm43xx: IRQ_READY timeout
[   50.388000] NET: Registered protocol family 10
[   50.388000] lo: Disabled Privacy Extensions
[   50.388000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.552000] usb 1-3: new low speed USB device using ohci_hcd and address 2
[   62.772000] usb 1-3: configuration #1 chosen from 1 choice
[   63.148000] usbcore: registered new interface driver hiddev
[   63.160000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input8
[   63.164000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:0b.0-3
[   63.164000] usbcore: registered new interface driver usbhid
[   63.164000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   66.636000] bcm43xx: IRQ_READY timeout
[   66.732000] bcm43xx: IRQ_READY timeout
[   66.828000] bcm43xx: IRQ_READY timeout
[   67.376000] bcm43xx: IRQ_READY timeout
```


(obviously not the whole dmesg, i truncated the stuff that shouldn't matter).

I don't know what else i could include, but i hope someone can steer me in the right direction!

---

