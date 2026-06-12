---
title: "EVDO card removal and reinsertion"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by vaxman- on 2008-04-24
I've followed the advice given in the PDF from this link:

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

I can connect with my Sprint EVDO card (PC5740 vendor=0x106c product=0x3701) without issue.  I used **lsusb** to get the vendor and product info as this card is not listed in the table in the PDF.

When I first insert the card, **sudo dmesg | grep -i ttyUSB** shows me two devices: **ttyUSB0** and **ttyUSB1**.  The modem works and I can connect.  However, if the card is removed and reinserted, only one devices, **ttyUSB0**, is created and the card cannot be used.  

Any tips as to how I can remove and reinsert the card without needed to reboot?

---

### Post by vaxman- on 2008-04-25
> **vaxman- said:**
> I've followed the advice given in the PDF from this link:

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

I can connect with my Sprint EVDO card (PC5740 vendor=0x106c product=0x3701) without issue.  I used **lsusb** to get the vendor and product info as this card is not listed in the table in the PDF.

When I first insert the card, **sudo dmesg | grep -i ttyUSB** shows me two devices: **ttyUSB0** and **ttyUSB1**.  The modem works and I can connect.  However, if the card is removed and reinserted, only one devices, **ttyUSB0**, is created and the card cannot be used.  

Any tips as to how I can remove and reinsert the card without needed to reboot?

I figured it out.  I needed to blacklist the cdc_acm driver.  Upon reinsertion, there would be 2 devices: ttyUSB0 and ttyACM0.

---

