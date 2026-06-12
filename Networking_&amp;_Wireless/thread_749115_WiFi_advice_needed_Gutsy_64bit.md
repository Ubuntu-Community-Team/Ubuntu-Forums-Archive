---
title: "WiFi advice needed Gutsy 64bit"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by old_dog on 2008-04-08
I have a "Shuttle SN25P" running 64bit gutsy I want to set up a wireless connection to an adsl/router. the only slot I have for a card is a mini pci-e. 
Can anybody recommend one of these that they have working on 64bit gutsy and what do I have to do to get it working?????
OR should I plump for a USB solution,indeed is there one for the above configuration again any advice welcome.
Cheers Guys
old_dog

---

### Post by hyper_ch on 2008-04-08
with my new adsl modem/router I got a usb wifi stick from netopia that worked out of the box (in hardy)... I'd think it will also work on 64bit gutsy but I have to look up which model it is at home.

---

### Post by old_dog on 2008-04-08
That will be great if you let me know the model
Thanks
old_dog

---

### Post by Mick8882003 on 2008-04-08
I have a belkin wap that didnt want to work with 64, had to drop back to 32 bit.

---

### Post by Paqman on 2008-04-08
You can get an Intel 3945 mini PCI-E off eBay for next to nothing. Should work "out of the box".

---

### Post by Sef on 2008-04-08
Moved to Hardy Heron.

---

### Post by hyper_ch on 2008-04-08
> **Sef said:**
> Moved to Hardy Heron.

He's using Gutsy...

---

### Post by hyper_ch on 2008-04-09
Now I checked it.

The model is a netopia USB Wireless LAN Card
Model: TER/GUSB-E
P/N: 8960049-00-01

and lsusb returns:
```

Bus 005 Device 003: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi

```

It works out of the box on hardy 32-bit.

---

### Post by LaRoza on 2008-04-09
Moved to Networking & Wireless.

Not sure why it was moved earlier, but due to the number of threads about Hardy that are moved, I understand how a thread could be moved by accident.

---

### Post by old_dog on 2008-04-10
Thanks HYPER_CH
I am fairly sure after the official release of Hardy I will re-install as 32bit I am a bit frustrated with 64bit
Once Again 
Thanks old_dog

---

### Post by hyper_ch on 2008-04-11
well, it's got a ralink chip and those are generally better supported... or go for INTEL PRO/Wireless chip... those work also excellent - however I have no experience with 64-bit OS.

---

### Post by raj727 on 2008-06-01
I also have a SN25P.  My SN25P is not a laptop but a PC with a micro-ATX board.  

Does anybody know if I can use the Intel 3945 mini PCI-E card in a standard PCI-E slot?

---

