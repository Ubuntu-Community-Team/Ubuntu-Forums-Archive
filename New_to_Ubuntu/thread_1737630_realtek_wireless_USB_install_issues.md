---
title: "realtek wireless USB install issues"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by cycle300 on 2011-04-23
Hello,
  Im the newest of the new with ubuntu. Im trying to install a USB Realtek wireless adapter. i ran LSUSB and i see it listed. but it didnt cant bring the device up. I downloaded the driver from the realtek site, but cant for the life of me figure out howto install it. i  unzipped it to a directory and then opened up a terminal and tried all these make commands and compile commands to get it going but nothing seems to be working. does anyone know howto compile this into a .deb package so its a quick install for me? its a realtek usb wireless adapter 8188CSU. please please please

---

### Post by mike555 on 2011-04-23
With the usb wifi plugged in, doesn't "System>Administration>Hardware Drivers " give you an option to get the driver?  of course you will need to be online .

---

### Post by cycle300 on 2011-04-23
no sir it did not

---

### Post by heyandy889 on 2011-04-23
> **mike555 said:**
> With the usb wifi plugged in, doesn't "System>Administration>Hardware Drivers " give you an option to get the driver?  of course you will need to be online .
That would be my first "hunch," as well.

By the way, a command similar to lsusb is "lshw" or list hardware. In terminal, the terminal should prompt you to run the command with "sudo". FYI you can read more about the commands with the manual pages by running "man lshw"

One more suggestion, maybe you could try System>Administration>Update Manager. Ubuntu will prompt you for your sudo password because you can install and remove software. But yeah, the Update Manager lets you search for software updates, you'll need to be online for that to work, as well.

---

### Post by gandaran on 2011-04-24
>  its a realtek usb wireless adapter 8188CSU
is it really 8188CSU or 8188SU
if it is RTL8188SU I will have the solution for you.
better to post the output of
```
lsusb
```

---

### Post by cycle300 on 2011-04-24
i looked at the auction i bought it from. its actually 8188cus

---

### Post by Dutch70 on 2011-04-24
> **cycle300 said:**
> i looked at the auction i bought it from. its actually 8188cus

I believe he wanted you to post the output of...
```
lsusb
```

---

