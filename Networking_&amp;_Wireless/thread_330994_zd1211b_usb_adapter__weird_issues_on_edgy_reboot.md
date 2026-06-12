---
title: "zd1211b usb adapter  weird issues on edgy reboot"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by hawthorne on 2007-01-03
Hi,

I've finally got a ZD1211b based usb adapter to work with WEP using a stock edgy install. However.... when I reboot, the device is generates an error in dmesg

If I configure it live, 
**dmesg contains lines such as **
[17180513.376000] usb 1-1: USB disconnect, address 7
[17180513.376000] zd1211rw 1-1:1.0: error ioread32(CR_REG1): -22
[17180518.640000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[17180518.808000] usb 1-1: configuration #1 chosen from 1 choice
[17180519.020000] zd1211rw 1-1:1.0: firmware version 4725
[17180519.084000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-02-72 AL2230_RF pa0 g--
[17180519.088000] zd1211rw 1-1:1.0: eth1

and with suitable lines in /etc/network/interfaces and a couple of iwconfig and ifconfig commands, all is working well.

**BUT if I reboot, the usb device isn't seen properly (or that's what I think this is telling me  ](*,) **
[17179597.924000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17179601.036000] usb 1-2: device descriptor read/64, error -110
[17179616.252000] usb 1-2: device descriptor read/64, error -110
[17179616.468000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17179619.580000] usb 1-2: device descriptor read/64, error -110
[17179634.796000] usb 1-2: device descriptor read/64, error -110
[17179635.012000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17179645.420000] usb 1-2: device not accepting address 2, error -110
[17179645.532000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17179655.940000] usb 1-2: device not accepting address 2, error -110
[17179655.940000] usb 1-2: USB disconnect, address 2
[17179655.940000] zd1211rw: probe of 1-2:1.0 failed with error -110
[17179655.940000] usbcore: registered new driver zd1211rw
[17179656.052000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[B]
My wireless eth1 device is absent if I issue an ifconfig command.
If I disconnect the usb adpater and reinsert it, dmesg reports:[/B]

[17180513.376000] usb 1-1: USB disconnect, address 7
[17180513.376000] zd1211rw 1-1:1.0: error ioread32(CR_REG1): -22
[17180518.640000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[17180518.808000] usb 1-1: configuration #1 chosen from 1 choice
[17180519.020000] zd1211rw 1-1:1.0: firmware version 4725
[17180519.084000] zd1211rw 1-1:1.0: zd1211b chip 0ace:1215 v4810 full 00-02-72 AL2230_RF pa0 g--
[17180519.088000] zd1211rw 1-1:1.0: eth1
[17180519.456000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180583.624000] SoftMAC: Open Authentication completed with 00:14:6c:cf:34:b0
[17180583.652000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180593.804000] eth1: no IPv6 routers present

then all I do is issue the iwconfig and ifconfig commands again and all is well. Interface eth1 shows up again and works OK.

Any ideas how I can force Ubuntu to "disconnect" the usb wireless adapter while the system is fully booted and then do a virtual reinsert of the device? Or is there another way?

Has anyone got any ideas to solve this?
TIA

---

### Post by Smu on 2007-04-10
I'm having the exact same problem. Hopefully feisty will fix it...

---

### Post by sheen on 2007-10-25
I reup the topic, I have exactly the same problem with Ubuntu 7.10.
This is the only issue I have with Ubuntu, I need to resolve it : /

---

### Post by sheen on 2007-10-26
A little bump....

---

### Post by udude on 2007-12-28
Same here, with 7.10 running 2.6.22-14-generic.
In addition I can report that often I encounter system freeze (Gnome hangs) a few hours after the device is connected.
In other cases the mentioned error is appended to the kernel log a few times a second. Disconnecting/reconnecting the device does will not fix the problem so reboot is needed.

---

