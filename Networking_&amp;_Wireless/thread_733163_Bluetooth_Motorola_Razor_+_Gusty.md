---
title: "Bluetooth: Motorola Razor + Gusty?"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by bushwacker on 2008-03-23
I'm trying to connect my Motorola Razor V3 to my Dell Inspiron e1505 laptop via bluetooth, but I'm having some trouble, primarily because I don't know how to verify that the hardware on my laptop is configured properly. The bluetooth kernel module is loaded, and I have the bluetooth management service loaded on boot-up. When scanning for devices from my phone, I can pick up one device, but it's someone else's PC, not mine.

What steps do I need to take to ensure that my bluetooth device on the laptop is A) really up, and B) configured correctly? The existing tutorials I've found have either been USB centric, or claimed that it should "just work." 

Any help would be greatly appreciated.

---

### Post by grenness on 2008-03-23
Have you tried performing a scan the other way around, i.e. from your PC?

In terminal, type

```
hcitool scan
```

If bluetooth is working, it should report all visible bt devices nearby.


~Christopher

---

### Post by bushwacker on 2008-03-23
Chris, I tried this, and it said "no such device." My phone appears to be set up correctly, and it was in 'discovery mode' at the time, so the problem seems to be w/ my laptop. How do I verify that the bluetooth device is actually activated and/or configured right?

My bluetooth device, as well as my memory card reader and firewire port were disabled when I initially installed Gusty on my pc. All of these devices are not recognized (afaik) by the system, though their kernel modules are installed (presumably this is just a default). The root of the problem may be that I need to force ubuntu to redetect my hardware? How do I go about doing this? The one nice thing about SuSE and Fedora is that they have automatic hardware detection daemons that check for new devices on startup.

Thanks for the help so far, btw.

---

