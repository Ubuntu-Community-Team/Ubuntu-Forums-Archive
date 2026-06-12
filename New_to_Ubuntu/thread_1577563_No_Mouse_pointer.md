---
title: "No Mouse pointer"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-09-19
I recently installed 10.10 onto an older Toshiba Satelite laptop

All went well, except that there is no mouse pointer with either the touchpad or USB mouse..

As you move the mouse around you can see when it sits over icons.Click and drag workes . The only way I have been able to tell were the mouse pointer is is to press Ctrl ( set in System/pref/mouse )which gives a brief indication of where it is

---

### Post by alzie on 2010-09-19
I had a similar issue, it seems to me that installing the hardware driver for my video card solved this.

>System>Administration>Hardware Drivers  should give you a list a drivers for your video card.  I always start with current.

I hope this helps.

---

### Post by Ducatiboy Stu on 2010-09-22
Problem turned out to be a USB port issue, seems it was a conflict with a USB port expander. Once I disconnected the other USB devices the pointer came to life. The pointer remained after the other USB devices where re-connected, even after re-booting with them connected

---

