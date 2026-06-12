---
title: "setting up a 3G dongle"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2010-08-07
Hi guys
Does anyone have experience setting up a 3g dongle with ubuntu (10.04)
I've just had a mate call me asking me if I can help set it up.

All I know at this point is its on 3,
Any tips before I get started would be much ppreciated.

---

### Post by redbook4574 on 2010-08-07
In general I find most 3g dongles just work in ubuntu, the only catch being they normally need to be activated via windows first.

---

### Post by bigmonmulgrew on 2010-08-07
how do I activate them?

---

### Post by patC42 on 2010-08-07
I am having trouble connecting to 3connect directly with ubuntu so I start it in windows and then restart ubuntu 10.4 without disconnecting it in windows - and it works.

---

### Post by 3rdalbum on 2010-08-07
> **patC42 said:**
> I am having trouble connecting to 3connect directly with ubuntu so I start it in windows and then restart ubuntu 10.4 without disconnecting it in windows - and it works.

It sounds like you need to locate some firmware for it to work in Ubuntu. Windows is loading the firmware to the device, and the firmware persists in the device across a reboot (as long as it doesn't lose power).

If you find the correct firmware and put it into your /lib/firmware folder, you'll be able to use the device straight away in Ubuntu.

---

