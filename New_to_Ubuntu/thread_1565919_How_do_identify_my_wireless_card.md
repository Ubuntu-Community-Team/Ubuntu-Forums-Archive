---
title: "How do identify my wireless card?"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by jinba.ittai on 2010-09-01
wlan1? wlan0? Trying to identify it in terminal and it keeps returning "no such device found". I know its working cause i can connect to wifi with it. (its a usb card)

---

### Post by Smart Viking on 2010-09-01
Usb card, then i think it would be somewhere in the output of this command:

```
lsusb
```
:)

---

### Post by AlphaLexman on 2010-09-01
If you can connect to wi-fi,
```
ifconfig
```
should identify it also.

---

### Post by jinba.ittai on 2010-09-01
> **AlphaLexman said:**
> If you can connect to wi-fi,
```
ifconfig
```
should identify it also.

Thanks, figured out there are two,exactly what i needed for the wlan0 and 1! 

> **Smart Viking said:**
> Usb card, then i think it would be somewhere in the output of this command:

```
lsusb
```
:)

Thanks! That  helped in determining the name and driver of my cards

---

