---
title: "Nintendo Wi-Fi USB Connector not seen on Feisty"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by scottywz on 2007-06-23
Hi, I'm trying to get the Nintendo Wi-Fi USB Connector working on one of my Feisty machines.  It worked out of the box on my laptop, but I really need it to work on my other machine.  (Both are Feisties.)  The problem is, on this one, it doesn't see the stick (an rt2570) under lsusb, and dmesg says nothing about it.  I tried building the rt2570 drivers using module-assistant, but it didn't work.

The one I'm having problems with doesn't have built-in Wi-Fi, for the record.

What's wrong?

Thanks, Scot

---

### Post by scottywz on 2007-06-24
Ok, now my laptop isn't seeing my Atheros wireless card.  iwconfig says:

```
lo        no wireless extensions.

eth0      no wireless extensions.

vnic0     no wireless extensions.
```

Normally the Atheros card shows up as ath0.  Any ideas?

---

### Post by scottywz on 2007-06-24
Ok, rebooting my laptop fixed that problem, but the other computer still isn't seeing the USB connector.  My laptop still sees it just fine.  I'd really appreciate any help with this issue.  Thanks.

---

### Post by scottywz on 2007-06-24
I fixed it by plugging it into a different port.

---

