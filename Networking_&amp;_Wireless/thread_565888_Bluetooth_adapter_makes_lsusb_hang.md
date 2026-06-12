---
title: "Bluetooth adapter makes lsusb hang"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by akb on 2007-10-02
Hi there,

I am trying to set up my brand new Belkin Bluetooth 2.0 Class 1 adapter right now, but got stuck right at the beginning: It gets recognized by /var/log/messages, but doesn't seem to get registered as a bt device. Calling hciconfig or hcitool dev both tells me there's no device, checking with lsusb doesn't even work, as lsusb just hangs without any output as long as the dongle is plugged in. When unplugging it lsusb continues to react and lists the other devices... but I don't seem to get a chance to take a look at the dongle itself.

The only thing I have for troubleshooting is dmesg:

```
Oct  3 01:40:33 localhost kernel: [ 7653.687037] usb 4-2.7: new full speed USB device using uhci_hcd and address 6
Oct  3 01:40:33 localhost kernel: [ 7653.803801] usb 4-2.7: configuration #1 chosen from 1 choice
```
When loading ehci_hcd it tells the same with ehci_hcd instead of uhci_usb, but it doesn't change anything.

So... is there anyone who got an idea about this?

Thanks in advance

Arne

---

### Post by linuxwizard on 2007-10-03
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by akb on 2007-10-03
Thanks, but that doesnt cover my specific type of problem, as I don't need to know how to set up the bluetooth environment but how to get the device itself working. Without the device showing to the bluetooth handlers nor a working lsusb I can't do anything.

---

### Post by Wiehan on 2008-01-03
Have you tried blacklisting the pegasus driver by adding "blacklist pegasus" to the /etc/modprobe.d/blacklist? That did it for my belkin dongle.

---

### Post by zinho on 2008-01-18
Yeah Wiehan!! Your fix work for me!!

Thanks!!

:guitar:

---

### Post by awnishUpadhyay on 2008-01-23
Thank you very much...i was able to solve the problem...finally my belkin usb adaptor is recognised and is working finne.....thank you for ur valuable tips...

---

### Post by lothar_m on 2008-02-20
> **awnishUpadhyay said:**
> Thank you very much...i was able to solve the problem...finally my belkin usb adaptor is recognised and is working finne.....thank you for ur valuable tips...

mine too. it's working great. thanks for all the help.

---

