---
title: "USB Keyboard"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Avalanche21 on 2009-01-26
When I am in BIOS I have no issue using my USB Keyboard but when I am on the Screen to choose to boot to Windows or Linux I am unable to use it. I can plug in a non-USB and it will work fine. Anyone know how I can fix this?

Thank you in advance!

Av

---

### Post by xpod on 2009-01-26
There should be a option in your bios settings to allow USB keyboards.

---

### Post by kestrel1 on 2009-01-26
You may have to also set it in your BIOS to enable legacy USB as well.

---

### Post by xpod on 2009-01-26
[https://help.ubuntu.com/community/InstallUSBKeyboard](https://help.ubuntu.com/community/InstallUSBKeyboard)
:)

---

### Post by marcgh on 2009-01-26
In the BIOS there should be an option " Legacy USB support ".
If you enable this it should be ok.

---

### Post by Avalanche21 on 2009-01-26
Hmmm strange. When I go into BIOS, I don't have an option for "USB Keyboard Support", "USB Legacy Support", nor PNP mode. All I have is "Resources Controlled By" and it is set to 'Auto'.

Av

---

### Post by Avalanche21 on 2009-01-26
OK for people who may have the same issue that I had I will tell you where I found this option in BIOS. If you find yourself going to the link that xpod gave me (about 3 posts up) and the paths are not the same, this is where I found mine.

Integrated Peripherals>OnChip PCI Device>USB Device Setting>
-USB functions - Enabled
-USB Keyboard Support Via - BIOS

I hope this helps someone.:p

Thank you everyone for your assistance.

Av

---

