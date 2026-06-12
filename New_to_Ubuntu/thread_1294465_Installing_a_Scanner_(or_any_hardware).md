---
title: "Installing a Scanner (or any hardware)"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Don Bowen on 2009-10-18
I have a scanner hooked up to my desktop computer.  How do I get Ubuntu to recognize it?

Is there a "hardware mgr" to look at like in windows?  How do you know when you're missing a driver for something?

---

### Post by MelDJ on 2009-10-18
most things run out of the box. just try scanning something

---

### Post by halitech on 2009-10-18
> **Don Bowen said:**
> I have a scanner hooked up to my desktop computer.  How do I get Ubuntu to recognize it?

Is there a "hardware mgr" to look at like in windows?  How do you know when you're missing a driver for something?

if its hooked up by a usb cable, open a terminal and run
```
lsub
``` and see if its listed.

as far as how to know if you are missing a driver, try to use the device and if it works, you have the driver, if it doesn't, you are missing the driver :)

---

### Post by falconindy on 2009-10-18
'lsusb' is the proper command. Scanners can be tricky, but often it just comes down to dropping a firmware file in the right place and XSane (Scanner Access Now Easy) will do the rest.

---

### Post by halitech on 2009-10-18
> **falconindy said:**
> 'lsusb' is the proper command. Scanners can be tricky, but often it just comes down to dropping a firmware file in the right place and XSane (Scanner Access Now Easy) will do the rest.

D'oh, thanks for catching that for me, fingers were ahead of my brain and didn't proofread what I typed :(

---

### Post by Don Bowen on 2009-10-20
> **MelDJ said:**
> most things run out of the box. just try scanning something
Yep!  That was it.  I scanned something and it worked the first time.  Wow!  Thank you for your patience with me not knowing that it already worked.

---

