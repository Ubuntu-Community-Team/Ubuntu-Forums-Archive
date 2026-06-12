---
title: "Turn on wireless card"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by SedukiDude on 2010-07-29
I am trying UBUNTU using a thumb drive and I am unable to turn on my wireless card on my Dell Inspiron E1505. I am attempting to load UBUNTU in Spanish. My normal way of turning on the wireless card is to press Fn and F2 when I am in Windows. For some reason it will not recognize this keystroke in UBUNTU.

---

### Post by Paddy Landau on 2010-07-29
I'm not sure whether this will help.

You should see a networking icon on your panel. Right-click and select "Enable Wireless".

---

### Post by dustinmarlowe56 on 2010-07-29
i am using a dell inspiron 1501. most dell models use proprietary drivers for wireless, so you will have to go to i think system>administration>hardware drivers to activate it

---

### Post by anewguy on 2010-07-29
I suspect you need the driver for your wireless first.  To help us see which driver you need, we need to see some detail on your hardware.  Please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

lspci <press enter>

lsusb <press enter>

lshw -C network <press enter>

Copy/paste the output in a reply back here.

Dave ;)

---

