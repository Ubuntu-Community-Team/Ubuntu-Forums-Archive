---
title: "[SOLVED] E172 USB Modem - Modem not detected"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by mundo on 2008-08-17
Hi,

If I do a sudo wvdial then I get this:

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

My USB modem has a built in micro SD card so I think it recognises it as a storage device and not a modem.  How do I change this?

---

### Post by GeorgeVita on 2008-08-18
Hi,
your modem possibly is connected as /dev/ttyUSB0 (and not as /dev/modem) so you have to edit the /etc/wvdial.conf.

Read my post at ubuntuforums.org/showthread.php?t=891488

Your wvdial.conf must have some lines like:

[Dialer hspa]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","internet" 

Note that Phone, Username, Password and "internet" work for most providers, if not for yours ask them or give me feedback.
  
Connect with terminal command: sudo wvdial hspa
Disconnect by closing the same terminal window or Ctrl-C, wait for "disconnect" message and then close window.

bye

---

### Post by mundo on 2008-08-18
Hi GeorgeVita,

I have managed to get this working before but I've just had to do a reinstall and didn't document how I did this.

I already have my wvdial as you have described but I seem to remember having to do something to tell Ubuntu to see my card as a modem and not a storage device.

---

### Post by GeorgeVita on 2008-08-18
Hi,
I have tested that when you have a good Ubuntu 8.04 installation, the only you need to use the Huawei modem is the wvdial.conf and the sudo wvdial hspa (in my example). You can test that the modem is on USB port by typing lsusb at the terminal window. The storage device it will appear at desktop and if you want you can "eject/remove" it. If you want pass me your wvdial.conf (all text) and also the result of the lsusb command.

---

### Post by mundo on 2008-08-18
Thanks, I will do this tonight and post my results.

---

### Post by mundo on 2008-08-18
I got it to work by changing:

"Modem = /dev/ttyUSB0" to "Modem = /dev/ttyUSB1"

in the wvdial.conf file.

---

