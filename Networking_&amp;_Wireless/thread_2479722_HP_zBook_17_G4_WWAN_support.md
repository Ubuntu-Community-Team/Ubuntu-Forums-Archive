---
title: "HP zBook 17 G4 WWAN support?"
date: 2022-10-04
forum: Networking &amp; Wireless
---

### Post by Stefan_Grnberg on 2022-10-04
Hi.
I was about to install Ubuntu Budgie on my work laptop, but i couldnt find a way to get the live usb to find and enable the wwan module (not an usb dongle).
Its an hardware addon right on the mainboard of the laptop.
The module is Intel XMM 7360 LTE-A.

Any suggestions how to possible get the wwan to work in ubuntu (budgie)?

Thanks in before hand.

---

### Post by mIk3_08 on 2022-10-05
> **Stefan_Grnberg said:**
> Hi.
I was about to install Ubuntu Budgie on my work laptop, but i couldnt find a way to get the live usb to find and enable the wwan module (not an usb dongle).

What version of Ubuntu Budgie live usb did you try to load in your laptop?
Is this the testing part of the live usb your about to tell us? 
if the live usb can't run the hardware then its the hardware that is not supported yet. 
[Click Here]("https://github.com/intel/linux-intel-lts/issues/7") for more info. Regards and cheers

---

### Post by Stefan_Grnberg on 2022-10-06
> **mIk3_08 said:**
> What version of Ubuntu Budgie live usb did you try to load in your laptop?
Is this the testing part of the live usb your about to tell us? 
if the live usb can't run the hardware then its the hardware that is not supported yet. 
[Click Here]("https://github.com/intel/linux-intel-lts/issues/7") for more info. Regards and cheers


Yesterday i found this [https://github.com/xmm7360/xmm7360-pci](https://github.com/xmm7360/xmm7360-pci)
This worked for me, altho, its not persistant between reboots, it works 100% for me.
Someone how know how to and can, might be able to turn this into a kernel module or a service, and get it into network manager, i cannot.

---

