---
title: "HELP with Huawei E156G Modem on 10.04"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by folabiklan on 2010-06-01
[FONT="Book Antiqua"][/FONT]
hi please i use 10.04 LTS ubuntu variant and a Huawei Usb Modem ( E156G)

i have since noticed that the only way i can get network manager to recognise the modem and be able to dial up from network manager is when i plug in the modem before starting the system, or when i reboot with the modem plugged in!

it works fine when it dials, but whenever it disconnects, or i remove it and plug it back in, it will not be recognised by network manager, the notification thingy will pop up but i cant find it in network manager.

i have tried to restart network manager but to no avail.
i have also tried to install usbmodeswitch, but it made no difference (mind the modem worked without modeswitch anyway)


please i need help. i cant be restarting my pc, right in the middle of important work all the time.

---

### Post by gandaran on 2010-06-01
did you run any commands from a mobile internet setup guide?
I had exactly the same problem after trying anything to get my mobile internet working, I knew what had happened but instead of trying to fix it I just reinstalled Ubuntu!
type this command in terminal to check if 'usbserial' module is loaded at start-up or when you plug in the dongle. 
```
lsmod
```

---

### Post by paulfiske on 2010-06-22
I have exactly the same problem! I also installed usb-modeswitch, but the haphazard recognition of the usb dongle has continued. I have resigned myself to restarting the computer with the huawei dongle connected! Frustrating, though, as I like Ubuntu 10.04!

---

