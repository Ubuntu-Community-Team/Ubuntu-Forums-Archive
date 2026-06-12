---
title: "USB Wireless Device"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Sethalos on 2009-03-16
Hola,

I have a USB Wireless device that I use to connect to the internet pretty much anywheres. I want to know if anyone has had any problems connecting with it. I can't seem to find a linux driver for it, and was just wondering if anyone knows where this can be found, or IF it can found.

It's a BELL Canada device if that helps.

Seth

---

### Post by aeiah on 2009-03-16
Bell Canada probably make more than one device, so no, it doesn't really help. In fact, they probably dont make any devices, they just repackage other people's stuff with their branding.

open a terminal and do ```

lsusb

```

(thats a lowercase L by the way)

this will list details of all your usb devices that are currently powered. it should give you enough details to either reply back here with a more specific description of your wireless card or find ways to get this working under ubuntu.

---

