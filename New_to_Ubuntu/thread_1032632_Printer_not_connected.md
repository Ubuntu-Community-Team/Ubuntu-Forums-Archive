---
title: "Printer not connected????"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Pappy1911 on 2009-01-06
Hi folks.

Just connected my HP 2500l color laserjet via a USB cable.
Unbuntu reconized printer and went through the install process. Final step was to print test page.
I said yes and I get an error message, Printer not connected.  
I re-pluged cable at both ends and still same message.
From system log;

Jan  6 14:51:18 johnny1911-desktop python: hp-toolbox[6587]: error: Unable to communicate with device (code=12): hp:/par/hp_color_LaserJet_2500?device=/dev/parport0

Any help??? Thank you..

---

### Post by ubudog on 2009-01-06
Open a terminal and type lsusb and paste the results in a reply.

---

### Post by Pappy1911 on 2009-01-06
johnny1911@johnny1911-desktop:~$ lsusb
Bus 005 Device 006: ID 08ec:0020 M-Systems Flash Disk Pioneers 
Bus 005 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 03f0:1424 Hewlett-Packard f2105 Monitor Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 03f0:0717 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
johnny1911@johnny1911-desktop:~$

---

### Post by ubudog on 2009-01-06
The computer sees that it's there. Try searching google for a driver.

---

### Post by Pappy1911 on 2009-01-06
Thanks..this will take some time...

---

### Post by ubudog on 2009-01-06
Anytime

---

### Post by Pappy1911 on 2009-01-06
I'm getting a headache over this.....more tomorrow..

---

