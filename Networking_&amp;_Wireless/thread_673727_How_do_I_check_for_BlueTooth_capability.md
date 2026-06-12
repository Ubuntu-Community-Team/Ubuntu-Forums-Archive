---
title: "How do I check for BlueTooth capability?"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by pieisgood on 2008-01-20
I don't know whether or not my computer has blue-tooth built in. Is there any way I can check? searching devices doesn't bring up anything ... maybe I'm just being hopeful.

---

### Post by steveneddy on 2008-01-21
According to[ this thread]("http://ubuntuforums.org/showthread.php?t=586105"), you would use these commands to check for bluetooth.

First use** lsusb** to check for a bluetooth adapter.

The command** hcitool dev** will tell you the bluetooth device address.

---

### Post by pieisgood on 2008-01-21
Ah, thank you. Looks like I don't have a bluetooth device! HAHA!

pieisgood@pieisgood-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
pieisgood@pieisgood-laptop:~$ hcitool dev
Devices:
pieisgood@pieisgood-laptop:~$ 


Oh well

---

### Post by steveneddy on 2008-01-21
Many times you can add bluetooth to any PC by buying either a mouse or keyboard with the bluetooth adapter that you plug into a USB port, or just the USB adapter itself.

---

### Post by pieisgood on 2008-01-21
Yeah, that's what I plant to do now I guess. I was just trying use my 360's wireless controller as a mouse. If that is even how it would go about. I don't have the room for a regular mouse and the track pad on my laptop is the devil.

---

