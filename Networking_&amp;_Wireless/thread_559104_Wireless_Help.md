---
title: "Wireless Help"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by cbk1994 on 2007-09-24
I have a D-Link AirPlus DWL-G510 card. It worked fine on Windows. Now I need it for Ubuntu.

I have no idea how to install it. Can someone please help me? Thanks so much in advance!
Chris

---

### Post by anagor on 2007-09-24
what version of ubuntu are you using?
and what is the chipset on your wireless card?
you can write: 
lspci -nn
in the console and look for your card's name there, 
if its there, its tells that the card was recognized by the kernel, and you will see near the end of the line hex numbers like this: 10de:0264
along with revision number:  (rev a3)

post this info so we can know more about your kernel version and the exact model of your DWL.

if its not there it tells us that the kernel didn't recognize the card, but all is not lost, it just will be a little harder to get it working. the same hex numbers by the way can be obtained from windows, it's the Vendor_ID and Product_ID in the driver property's advanced tab I think, in the hardware manager in My Computer properties application.

---

### Post by cbk1994 on 2007-09-24
Okay, I will try that and post my results ASAP. Right now I can't get to the computer, but tomorrow I'll be able to.
Thanks so much!

---

### Post by cbk1994 on 2007-09-26
I am using the latest version of Ubuntu (7.04)

It does not show the card. However, on Windows it says that it is the same card I mentioned (D-Link AirPlus G DWL-G510 Wireless PCI Card), but not the revision, and I can't find it anywhere else. Does this mean first revision?

Thanks so much!
Chris

---

### Post by cbk1994 on 2007-09-26
Also, I just checked the box it came in, and it says Ver1.00 on a side flap of the box.
Chris

---

### Post by cbk1994 on 2007-09-27
I really need to get this fixed ... does anyone have any ideas? If I can't get this fixed by tomorrow I have to wipe Ubuntu and install Windows.

---

### Post by cbk1994 on 2007-09-29
Please, surely someone has an idea?

---

### Post by cbk1994 on 2007-10-02
bump

---

