---
title: "Billionton Bluetooth dongle"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Marsan on 2006-11-11
Hello!

I have a Billionton Bluetooth dongle and i dont get it to work. lsusb dont detect it either so i was woundering if it actually works in Ubuntu (edgy).
The product number on the dongle is: UBTBR2

Come to think of it, it newer worked on Windows either so i would be suprised i get it to work.

Anyone hawe any tips?

Im happy for replys :D

Marsan

---

### Post by adwait on 2006-11-11
Plug it in to the USB port.....normall, Ubuntu will detect it and tell you that a Bluetooth dongle has been detected. If it doesn't, try runnig the command
```
lsusb
```

See if it shows your device in the list there.

---

### Post by Marsan on 2006-11-11
As i wrote in the first post, lsusb dosent show my bluetoothdongle.

---

### Post by wieman01 on 2006-11-11
Strange... Billionton is a brand generally recognized by Ubuntu. Got one myself. But if it did not work in Windows, there is a good chance something is wrong with it.

Can you run "lsusb" before you plug in the dongle and then run it again after you have done so? Perhaps it appears under a misleading name... If it does not show at all, I'll shut up. ;-)

---

### Post by Marsan on 2006-11-11
before:

```
marsan@marsan-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
```

after:

```
marsan@marsan-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  

```

---

### Post by wieman01 on 2006-11-11
OK, then I am afraid there is not much we can do. I would try it on another machine & see if it is recognized (by either Windows or Ubuntu). If not, you know what you have to do (go & buy a new device). :-)

---

### Post by i.shaddix on 2008-01-07
I have a Billionton Bluetooth dongle that would not work on Ubuntu 7.06. This is what I get when I with lsusb:
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 015: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 014: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 013: ID 0a5c:2100 Broadcom Corp. 
Bus 004 Device 012: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 001: ID 0000:0000  

I can see that it is detected by Ubuntu, but how can I make it work? Nothing appears when I connect the dongle to the usb port. Please help. Thanks

---

### Post by Thanh-BKK on 2008-04-27
Hello.

This is an older thread, but i just happen to have the identical problem. Ubuntu 8.04 Hardy, "Billionton" bluetooth dongle.

Here's my lsusb:

thanh@thanh-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 066f:4200 SigmaTel, Inc. STIr4200 IrDA Bridge
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 0000:0000  

The IrDA thingy is detected and working, as is the printer/scanner but the Billionton isn't even found.

The same Billionton, sitting in the same USB port, is working fine on both Windows Vista and Windows XP which i have dual-booting on another HDD (which i swap out for Linux). 

Any help is greatly appreciated (i don't want to buy another dongle because as long as i still use Windows, too, i don't want to have to mess with the drivers there). 

Best regards......

Thanh

---

