---
title: "can't boot up when plug with Huawei E1550 modem"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by cloube on 2011-01-22
Hi ,

i'm using Huawei E1550 modem to connect to the internet. i face problem just now during the startup, i plug my E1550 modem to the PC. but the page got hang on the bios selection page (press F2 to select bios). i tried several times,and i figure out it might be because of usb modem connected to the pc as previously i have problem on installing via wubi which pop out pyrun.exe error. when i unplug the modem and restart the pc, it work well and able to login into ubuntu.

I just need some information on where i could check the log of this and to confirm what's the problem are about. im in the phase of exploring ubuntu and its platform.anyone can give me some guide or idea?

---

### Post by zeroseven0183 on 2011-01-22
Does this happen only when the USB modem is plugged in during boot time? How about any other USB device?

You may want to check the boot priority settings in the BIOS.

---

### Post by cloube on 2011-01-22
i havent test with other usb related device. i might try that letter. for bios, i just set first priority to DVD-ROM then C drive .when the modem is connected,i can't log even to the bios. the PC seem to be hang and no blinking read fom either the DVD drive or C drive.

---

### Post by cloube on 2011-02-03
> **zeroseven0183 said:**
> Does this happen only when the USB modem is plugged in during boot time? How about any other USB device?

You may want to check the boot priority settings in the BIOS.


as far as i  check. i only have problem when huawei E1550 modem is connected to the laptop. for my bios setting, i dont have usb as first boot device in the settings.curent setting for booting device is C,DVD and floppy...

---

### Post by sandyd on 2011-02-03
how old is your laptop?

---

### Post by cloube on 2011-02-12
around 6 years

---

