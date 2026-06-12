---
title: "kbluetooth keeps crashing in Gutsy"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by ger_macaco on 2008-01-10
Hi, I am running Kubuntu 7.10 in a AMD64 platform. I've got my bluetooth dongle always connected to the USB port.

Everytime I boot, kbluetooth crashes and I'm not able to use it.
It also crashes if I try to start it afterwards.

Here's what I'm getting:

```
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47827795548320 (LWP 8273)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00002b7fc28ad4f9 in QString::latin1 () from /usr/lib/libqt-mt.so.3
#6  0x00002b7fc28b068b in QString::ascii () from /usr/lib/libqt-mt.so.3
#7  0x00002b7fbf32a27f in KBluetooth::DBusSignal::newMessage ()
   from /usr/lib/libkbluetooth.so.0
#8  0x00002b7fbf32b20c in KBluetooth::DBusSignal::getString ()
   from /usr/lib/libkbluetooth.so.0
#9  0x00002b7fbf32b3dd in KBluetooth::DBusSignal::getString ()
   from /usr/lib/libkbluetooth.so.0
#10 0x00002b7fbf326986 in KBluetooth::Adapter::getMode ()
   from /usr/lib/libkbluetooth.so.0
#11 0x000000000041477c in ?? ()
#12 0x00000000004169b3 in ?? ()
#13 0x0000000000417c4e in ?? ()
#14 0x0000000000416d45 in ?? ()
#15 0x00002b7fc5eafb44 in __libc_start_main () from /lib/libc.so.6
#16 0x000000000040fda9 in ?? ()
#17 0x00007fffeb9cc498 in ?? ()
#18 0x0000000000000000 in ?? ()
```

Any ideas?

---

### Post by kaktuskatta on 2008-01-10
Hi! I also experienced this problem. My solution was to disconnect from wlan, and for some reason that helped :-S That means that I can't be online on an wireless connection while using my wireless NIC, but I don't mind the few minutes we're talking about. I have an Intel Pro Wireless card for laptop, but why don't you give it a try? :)

---

### Post by ger_macaco on 2008-01-10
Many thanks for your answer.

I do not have wireless LAN. This is a desktop PC with cable LAN.

---

### Post by ger_macaco on 2008-01-10
Found out that if I boot without the USB dongle plugged and connect it after boot, it doesn't crash.

However, when I want to pair my cellphone (Moto L6), it asks me if I want to allow the cellphone to use **kbtobesrv** service.

After allowing it, the cellphone tells me that it was impossible to connect.

Any Ideas about this 2 issues?

---

### Post by jgbreezer on 2008-02-02
I'm getting this too, same backtrace results. I also have my bluetooth usb dongle plugged in (via an external usb hub) at boot; I'll try plugging it in after boot next time; a guess from the backtrace could be some character encoding thing, but haven't a clue how that could be affected/affect by the symptoms. Have a normal ethernet connection to my ADSL router.

---

### Post by ger_macaco on 2008-02-05
New kernel update seems to fix the on-boot crash.

edit: I was wrong. It didn't crash on the first 2 boots, but now it's happening again.

---

