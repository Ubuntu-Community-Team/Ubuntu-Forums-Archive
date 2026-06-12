---
title: "[ubuntu] cant update broadcom driver"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by mshafer-ms on 2014-08-28
so i just installed 14.04 LTS on an old laptop i had. i was using it booted off a usb drive and decided to install. when i was running off the usb the broadcom driver installed and worked just fine but now that ive installed it when i go to system SETTINGS>SOFTWARE & UPDATES>ADDITIONAL DRIVERS it shows the driver in this dialog but when i go to select it and apply changes it loads a bit then reverts to do not use the device. any help would be appreciated thank you.

---

### Post by chili555 on 2014-08-28
What is your Broadcom device? From a terminal:```
lspci -nn -d 14e4:
```When you are trying to apply the Additional Driver, are you connected to the internet?

Thanks.

---

### Post by mshafer-ms on 2014-08-29
typed lspci -nm -d 14e4
recieved lspci: -d ':' expected

---

### Post by mshafer-ms on 2014-08-29
and i cant connect to the internet cause the driver won t activate. its a broadcom bcm 4322 (rev 01)

---

### Post by mshafer-ms on 2014-08-29
finally got ahold of a wired connection and it finally activated the driver.

---

