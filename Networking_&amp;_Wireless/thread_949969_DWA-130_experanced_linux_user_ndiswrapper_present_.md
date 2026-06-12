---
title: "DWA-130 experanced linux user ndiswrapper present yes"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by geramy on 2008-10-16
hi right now im runing x64 Kubuntu and i would like to setup my DWA-130 usb dlink card im using a dlink DWL-G520 right now have been working on this for days almost brand new system usb-2.0 thanks for reading and replying.

---

### Post by cariboo on 2008-10-16
What is the output of:

```
sudo  lshw -C network
```

with your DWA-130 plugged in.

Jim

---

### Post by geramy on 2008-10-16
root@geramy:~# lshw -C network
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:8c:f2:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.116 latency=168 ma8 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
root@geramy:~#

---

### Post by geramy on 2008-10-16
> **geramy said:**
> root@geramy:~# lshw -C network
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:8c:f2:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.116 latency=168 ma8 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
root@geramy:~#
 and also you know about dual-core on kubuntu i dont think both are present annd the bus speed is 200mhz? i have hypertransport 1000mhz 1ghz

---

### Post by Ayuthia on 2008-10-16
Can you also post the results of lsusb?

---

### Post by geramy on 2008-10-16
Bus 002 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 07d1:3b11 D-Link System
Bus 001 Device 003: ID 03f0:031d Hewlett-Packard
Bus 001 Device 001: ID 0000:0000

---

### Post by Ayuthia on 2008-10-16
I was trying to link the usb device to the Atheros info in lsusb, but I am not able to do so.  However, I am seeing that lshw -C network is showing that ath_pci is being used instead of ndiswrapper and it is also assigned an ip address.  Do you have another wireless device?  I am guessing that the Atheros info is a wireless device because it is showing 802.11g which goes with wireless as far as I know.

If this is all correct, it looks like you are trying to use the ath_pci module instead of ndiswrapper.  Have you tried unloading the ath_pci and loading ndiswrapper instead?

---

### Post by geramy on 2008-10-16
no i dont no how to unload my pci card and yes i have one working its a AR5212 but i need dlink DWA130 working its a varvil chipset i think im running x64 system

---

### Post by Ayuthia on 2008-10-16
> **geramy said:**
> no i dont no how to unload my pci card and yes i have one working its a AR5212 but i need dlink DWA130 working its a varvil chipset i think im running x64 system

If that is the case, I would not unload the ath_pci module because that is for a different card.

I am not familiar with the dlink cards at this point so I can't really help much further.  Sorry.  You might try doing a search on 07d1:3b11 D-Link System and see if anything comes up.

---

### Post by geramy on 2008-10-16
the usb dlink DWA-130 is lit up just need instructions how top turn it on

---

### Post by cariboo on 2008-10-16
It looks like your PCI card is somehow interfering with the usb device. You could always pull your pci card from the computer and the try to set up your usb device. If pulling the card is beyond your expertise try this in a terminal:

```
sudo rmmod ath_pci
```

enter your password when asked. If everything went well, nothing will be echoed back. This will unload the driver for your internal wireless card while you get your usb device working. to reinstall the module, just restart your computer or in a terminal type:

```
sudo modprobe ath_pci
```

If you plan on using ndiswrapper, have the windows driver disk handy as you will need the .inf and .sys files.

Jim

---

