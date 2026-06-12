---
title: "Trying to install Alfa AWUS036H drivers"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by bob94 on 2014-08-15
I am new to linux and have been trying to install drivers to run a Alfa wireless usb adapter. I have downloaded the drivers and extracted the files in a folder on my desktop. file  rtl8187l_linux_1041.0209.2012 

I have tried various ways using the terminal but get error messages bash, file not found, not a valid command etc. I have used sudo install and others but no luck. If it was not a requirement for work to learn linux I think I would stick with win 7. 

Any suggestions on how to install the drivers as I cannot access the internet on the ubuntu computer. It is installed on an old computer and my only access to the internet is through wifi.

Thanks Bob

---

### Post by chili555 on 2014-08-15
In recent Ubuntu versions, rtl8187 is built-in and no compiling is required. What version are you running?```
lsb_release -d
```Please tell us more about your device:```
lsusb
dmesg | grep rtl
```

---

