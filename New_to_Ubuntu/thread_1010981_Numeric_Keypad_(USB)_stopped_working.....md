---
title: "Numeric Keypad (USB) stopped working...."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by thaumielx72 on 2008-12-14
I upgraded my Toshiba Satellite a215-s7416 notebook to Ubuntu 8.10.   For a while the usb device was working fine.  One of the updates must have crashed it.

thaumiel@thaumiel-laptop:~$ lsusb

Bus 006 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 002: ID 0951:1607 Kingston Technology Data Traveler 2.0
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thaumiel@thaumiel-laptop:~$ 

It appears to not even show up any more.  I know this seems like a silly complaint but I use my laptop mostly to input some long numbers for calculation and the external keypad makes that so much easier.

As crowded as the forums are today I figured someone might have an answer.

Thanks in advance for your time.

---

### Post by bluefrog on 2008-12-14
try <shift>  + <numlock>

can also have a look at system/pref/keyboard - accessibility uncheck "accessibility features"

---

### Post by thaumielx72 on 2008-12-14
Thanks for the reply but I'm using a laptop and there is no keyboard on it and so no numlock key. The keyboard preferences don't really refer to a usb plugin device.

---

### Post by bluefrog on 2008-12-14
yes sorry, went a bit fast on that one I have a numpad on my laptop.

sorry, don't know then.

---

### Post by jmmL on 2009-01-07
My numpad on my laptop stopped working as well. Not sure what caused it to, but have recently installed gsynaptics. At first I thought it might have been a hardware thing, but the key presses were still picked up by xev, which reassured me.

Anyway, that shift + numlock trick seems to have sorted it out.

Thanks!

---

### Post by AntiVista on 2009-07-04
Just installed ubuntu (freaking great, btw) and was having a similar issue with the built in numeric keypad, did a google search, found my way here.
 
Had a similar issue with my laptop (Compaq Presario CQ70-120US)) where the numeric keypad would drop out. Using SHIFT + NUMLOCK would wake it up, but have found that if I go to System>Preference>Keyboard>Layouts>Keyboard Model, I was able to load a keyboard model (Laptop/notebook Compaq (eg. Presario) Internet Keyboard) that was close to mine (one that had a numeric keypad) and the issue went away.
 
I'm a noob, so please feel free to flame away ;)

---

### Post by boroborolama on 2011-03-16
> **bluefrog said:**
> try <shift>  + <numlock>

can also have a look at system/pref/keyboard - accessibility uncheck "accessibility features"

Thank you!  Such a simple fix!  I've been dealing without the numeric keypad for months.  It just stopped working one day.  (I must have <shift> + <numlock> accidentally.)

---

