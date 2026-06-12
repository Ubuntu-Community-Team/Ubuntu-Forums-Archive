---
title: "install WL-167G v2"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by ErrUmm on 2009-12-18
Has anyone set up this wireless usb adaptor on Karmic? The ID shown using lsusb is 0b05 1723. The ralink site wont let me download anything , and the serial monkey site has indeciperable info for me anyway.
 
I am a complete n00b, so simple instructions please.

---

### Post by mehturt on 2010-01-03
I am using this adaptor with Karmic.  I can connect my WPA2 network and the connection is fine for a short time but then it degrades and makes the network unusable.

---

### Post by sandyd on 2010-01-03
> **ErrUmm said:**
> Has anyone set up this wireless usb adaptor on Karmic? The ID shown using lsusb is 0b05 1723. The ralink site wont let me download anything , and the serial monkey site has indeciperable info for me anyway.
 
I am a complete n00b, so simple instructions please.
according to 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus#USB)
it works - completely out of the box.
hmm....

---

### Post by mehturt on 2010-01-03
yes, that's why I bought it

---

### Post by sandyd on 2010-01-03
> **mehturt said:**
> yes, that's why I bought it
have you tried
```

sudo modprobe rt25

```
then ```
 ifconfig
```

post the output of that.

---

### Post by mehturt on 2010-01-03
right now, it seems setting the power management to "off" fixes the problem..

---

