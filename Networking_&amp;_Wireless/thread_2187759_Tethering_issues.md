---
title: "Tethering issues"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by too_tall on 2013-11-13
I have a laptop with vms on it.  One is 13.04 and I just created a new one with 13.10.

On my 13.04 I am able to tether my phone and use its Internet connection with no issues. This is what dmesg has to say:
```
[ 7251.705623] usb 3-2.1: new high-speed USB device number 11 using xhci_hcd
[ 7251.724560] usb 3-2.1: New USB device found, idVendor=22b8, idProduct=2e25
[ 7251.724567] usb 3-2.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 7251.724570] usb 3-2.1: Product: XT926
[ 7251.724573] usb 3-2.1: Manufacturer: motorola
[ 7251.724599] usb 3-2.1: SerialNumber: TA26102OPA
[ 7251.733502] rndis_host 3-2.1:1.0 usb0: register 'rndis_host' at usb-0000:03:00.0-2.1, RNDIS device, de:37:4a:2a:96:1a
[ 7267.458231] usb 3-2.1: USB disconnect, device number 11
```

On 13.10 when I try to turn on tethering, on the phone it shows it starts then stops almost immediately.  dmesg from the 13.10 box:

```
[15554.144198] usb 1-1: new high-speed USB device number 3 using ehci-pci
[15554.451913] usb 1-1: New USB device found, idVendor=22b8, idProduct=2e33
[15554.451919] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[15554.451921] usb 1-1: Product: XT926
[15554.451924] usb 1-1: Manufacturer: motorola
[15554.451926] usb 1-1: SerialNumber: TA26102OPA
[15563.638758] usb 1-1: USB disconnect, device number 3
```

Becasue this is one laptop and two vms, the hardware i sall the same, the only difference is the version of OS.

I can see I'm missing the rndis_host line.  I assume that defines my problem, but am really still new enough that I'm not sure how to go about fixing it.

Thank you in advance for any help anyone can give.

---

### Post by too_tall on 2013-11-17
I think I know where the problem is at least.

This seems to be an issue only with Gnome-Flashback.  Changed to Gnome classic asn all seems well now.

---

