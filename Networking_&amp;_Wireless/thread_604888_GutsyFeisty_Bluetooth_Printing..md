---
title: "Gutsy/Feisty Bluetooth Printing."
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by tmkt on 2007-11-06
I've looked for weeks, even months if we count my time with feisty.

Bluetooth printing just isn't working for me.
Followed all the steps
including Printing to bluetooth printers does not work with AppArmor enabled.
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/147800](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/147800)

when I click on print an item, I get prompted for the bluetooth pin.
I enter it, and then nothing happens.

I've tried printing from my cell phone to the bluetooth printer, and this works perfectly.

Using gutenprint drivers.

My printer is an Epson Stylus R380, and it is auto-detected by the gutsy printing software as bluetooth, with the correct mac address.

My cups errors logs have this one message
E [06/Nov/2007:20:06:27 +0000] PID 30295 (/usr/lib/cups/backend/bluetooth) crashed on signal 6!
/usr/lib/cups/backend$ ./bluetooth 
network bluetooth://0013105D4C1D "Unknown" "Stylus Photo R380-1 (Bluetooth)" "MFG:EPSON;CMD:ESCPL2,BDC,D4,D4PX,ESCPR1;MDL:Stylus Photo R380;CLS:PRINTER;DES:EPSON Stylus Photo R380;



I'm a do it yourselfer, and use message boards as a last resort, and here I am asking for a solution


Thanks,
Dave

---

